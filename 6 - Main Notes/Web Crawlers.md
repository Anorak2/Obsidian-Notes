
2026-03-30

Tags:[[Information Retrieval]]
# Web Crawlers
A crawler is an automated process that typically seeks visit every web page it can an index them, though details like it's traversal policies differ. This is usually done by starting with a few pages (seeds) and then traversing the links between these pages progressively. The pages crawled are put into an index where they are sorted based on the page size and the freshness.

## Crawler Requirements
- Be Polite: Respect implicit and explicit politeness considerations, such as only crawling allowed pages. This also means respecting `robots.txt`, but there is also implicit politeness where even without specifications the crawler tries to avoid hitting sites too often.
- Be Robust: Be immune to spider traps and other malicious behavior from web servers
- Be scalable: designed to increase the crawl rate by adding more machines
	- Performance/efficiency: permit full use of available processing and network resources
	- Be capable of distributed operation: designed to run on multiple distributed machines
- Fetch pages of “higher quality” first
- Continuous operation: Continue fetching fresh copies of a previously fetched page
- Extensible: Adapt to new data formats, protocols

## Steps

##  Architecture
![[Pasted image 20260420123133.png]]
- Parsing: Here we might have to do things like expand a relative URL into it's absolute URL
- Content Seen: There is a lot of duplication on the internet and especially with Links so if the page has already been indexed don't do further processing. This is usually done with document fingerprints or shingles, but this is harder than it might seem due to near duplicate pages.
- Filters: usually part of the filter is a regular expressions for URLs to be crawled/not. Also, once a robots.txt file is fetched from a site, no need to keep hitting it over and over again so we cache the robots.txt 
- For a non-continuous (one-shot) crawl, test to see if an extracted+filtered URL has already been passed to the frontier, for a continuous crawl it depends on the implementation


**Crawler Steps:**
1. Pick a URL from the frontier, there are a number of options for how to pick a URL such as Depth, Breadth, or Best first
2. Fetch the document at the URL
3. Parse the document and extract links from it to other docs (URLs)
4. Check if document has content already seen; If not, add to indexes
5. For each extracted URL first ensure it passes certain URL filter tests and then check if it is already in the frontier (duplicate URL elimination)

## Distribution
One of the big changes when we add distribution is determining who gets what. Part of that means adding a host splitter and the other part is combining the URLs from other nodes on duplicate elimination. Overall though, the individual nodes are independent and work is assigned statically apriori such as by web hash. The URL's are also dynamically assigned by the coordinator since it is more robust than static assignment.

Issues with static assignment include:
- Firewall mode: each c-proc only fetches URL within its partition – typically a domain and inter-partition links not followed
- Crossover mode: c-proc may follow inter-partition links into another partition this has a possibility of duplicate fetching
- Exchange mode: c-procs periodically exchange URLs they discover in another partition

![[Pasted image 20260420130231.png]]
In the Mercator scheme the front queue manages prioritization and the back queue manages politeness, each queue is FIFO.

**Front Queue**
Prioritizer assigns to URL an integer priority between 1 and K and then appends it to the corresponding queue. Some heuristics for assigning priority are refresh rate sampled from previous crawls and application-specific (e.g., “crawl news sites more often”)

**Biased Front Queue**
When a back queue requests a URL (in a sequence to be described) it picks a front queue from which to pull a URL. This choice can be round robin biased to queues of higher priority, or some more sophisticated variant and this can be randomized.

**Back Queue**
- Invariants:  Each back queue is kept non-empty while the crawl is in progress, and each back queue only contains URLs from a single host. Each host maintains a table from hosts to back queues.
- Heap: One entry for each back queue, the entry is the earliest time $t_e$ at which the host corresponding to the back queue can be hit again. This earliest time is determined from the last access to that host but can also have any other heuristic.
A crawler thread seeking a URL to crawl first:
- Extracts the root of the heap
- Fetches URL at head of corresponding back queue q (look up from table)
- Checks if queue q is now empty and if it is it pulls a URL v from front queues. If there’s already a back queue for v’s host, append v to it and pull another URL from front queues, repeat. Otherwise add v to q
- When q is non-empty, create heap entry for it

## Challenges
- JavaScript-heavy pages: fetching HTML may be insufficient without rendering
- Canonicalization is essential: canonical URLs, parameters, session IDs, and tracking variants
- Index selection: crawl != index (quality, spam, dedup, and crawl budget constraints)
- Sitemaps provide hints for discovery and freshness scheduling, but they are not always reliable.
# References