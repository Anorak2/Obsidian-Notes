
2026-03-30

Tags: [[Information Retrieval]] [[Algorithms]]
# Page Rank
Page rank is an algorithm based on the idea of a stochastic random walk based on the idea of an always on web server. The fundamental process is described below.
```markdown
Start at a random page
1. At each step, with probability 1-α, go out of the current page along one of the links on that page, equi-probably (randomly click on an out-going link)
2. At each step, with probability α, jump to a random page (input a URL to the browser) this is called teleporting
3. At a dead end, jump to a random web page.
Repeat forever
```

In the “steady state” each page has a long-term visit rate to be visited - use this as the page’s score, or PageRank. This is essentially an endorsement from the entire internet, rather than just from several websites.

## At time step N
If we start from a given node, then the initial probability distribution vector will simply be that row of the matrix (assuming row is the start node and column is the probability of transition from that node). To calculate this probability distribution vector at time t + 1 the stops are below
1. to calculate for node i
	1. take the dot product of the whole probability distribution vector and column i, this is functionally saying given the probability of being at each node what is the probability of transitioning to node i with a summation
## What position it holds
Complete Google ranking includes (based on university publications prior to commercialization)
- Vector-space similarity component.
- Keyword proximity component.
- HTML-tag weight component (e.g. title preference).
- PageRank component.
Unfortunately the current ranking systems are considered trade secrets.

# References
- [[Intro to Web Link Analysis]]