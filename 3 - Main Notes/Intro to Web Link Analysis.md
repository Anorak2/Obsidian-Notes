
2026-04-20

Tags: [[Information Retrieval]]
# Intro to Web Link Analysis
With the web we have an issue of how do we rank pages in order to answer user queries. There are conventional IR methods – e.g., TF/IDF which is how first generation web search engines worked, but there is a big difference between web pages and document repositories. The issue is that we want both high quality & important documents, a document repo generally has a more uniform importance distribution but this isn't the case with the internet.

## Web as a graph
Assumption 1: A hyperlink between pages may denote author perceived relevance and endorsement (quality signal)
Assumption 2: The anchor of the hyperlink often describes the target page (textual context)

**Anchor Text**
The idea is that Anchor text is a good brief for the target page. Can sometimes have unexpected side effects like spam artificially increasing the number of references. We get around this by scoring anchor text with weight depending on the authority of the anchor page’s website.  We trust anchor text from authoritative, trustworthy sources
```html
<a href=“http://www.ibm.com/”>Big Blue</a>
```

**Relevance and Importance**
Relevance, as conventionally defined, is binary (relevant or not relevant). It is usually estimated by the similarity between the terms in the query and each document. Meanwhile Importance measures documents by their likelihood of being useful to a variety of users, usually estimated by some measure of popularity. Web search engines rank documents by a combination of estimates of relevance and importance.

a big part of the game comes from how we calculate this importance
## Citation Analysis
Many standard documents have bibliographies (or references), explicit citations to other previously published documents. An easy example is scientific papers. Using citations as links, standard corpora can be viewed as a graph. The structure of this graph, independent of content, can provide interesting information about the similarity of documents and the structure of information.

Impact factor is one measure of this importance developed by Garfield in 1972 to measure the quality/influence of scientific journals. it's a measure of how often papers in the journal are cited by other scientists, Computed and published annually by the Institute for Scientific Information (ISI). The impact factor of a journal J in year Y is the average number of citations (from indexed documents published in year Y) to a paper published in J in year Y−1 or Y−2. However it doesn't account for the quality of the citing
article, and thus assumes a certain level of quality in order to get published.

##  Link Analysis
Web links are a bit different than citations:
- Citations to relevant literature is enforced by peer-review.
- Many links are navigational.
- Many pages with high in-degree are portals not content providers.
- Not all links are endorsements.
- Company websites don’t point to their competitors.
- A spammer could easily create 10000 pages and make all of them point to one spam page.

First generation used link counts as simple measures of popularity.
 Two basic suggestions:
- Undirected popularity: Score = number of in-links plus out-links (3+2=5).
- Directed popularity: Score of a page = number of its in-links (3).
Query Processing
- First retrieve all pages meeting the text query
- Order these by their link popularity
# References
- [[Page Rank]]
- [[Hyperlink-Induced Topic Search (HITS)]]