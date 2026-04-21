
2026-03-30

Tags: [[Information Retrieval]]
# Hyperlink-Induced Topic Search (HITS)
This is an algorithm developed by Kleinberg in 1998. It attempts to computationally determine hubs and authorities on a particular topic through analysis of a relevant sub-graph of the web. It's a very important as a conceptual model for hubs/authorities. However the algorithm is query-dependent, graph-subset dependent, and more fragile and spam-sensitive than PageRank-style global signals. HITS is best suited for “broad topic” queries rather than for page-finding queries.

**Hubs:**
a good hub page for a topic points to many authoritative pages for that topic.

**Authorities**
A good authority page for a topic is pointed to by many good hubs for that topic.

This is a circular definition, so for calculation we extract from the web a base set of pages that could be good hubs or authorities. From these, identify a small set of top hub and authority pages.

## Algorithm
Given text query (say browser), use a text index to get all pages containing browser. We can call this the root set of pages. From there we add in any page that either points to a page in the root set, or is pointed to by a page in the root set. We call this the base set. To eliminate purely navigational links we eliminate links between two pages on the same host.

Root set is about 200-1000 nodes.
Base set is up to 5000 nodes.

Compute, for each page x in the base set, a hub score h(x) and an authority score a(x).
- Initialize: for all x, h(x) <- 1; a(x) <- 1;
- Iteratively update all h(x), a(x);
- After iterations
	- output pages with highest h() scores as top hubs
	- highest a() scores as top authorities.
$$h(x) = \sum_{x\to y}(a(y)$$
$$a(x) = \sum_{y\to x}(h(y)$$

To prevent the h() and a() values from getting too big we can scale down after each iteration, but the scaling factor doesn't really matter. We only need the relative orders not the absolute values. These relative scores will also converge after only a few iterations, in practice it takes about 20 iterations.
# References
- 