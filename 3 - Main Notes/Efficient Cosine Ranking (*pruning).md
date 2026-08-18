
2026-02-16

Tags: [[Information Retrieval]]
# Efficient Cosine Ranking
In a vector space model computing the score can take a large amount of work on the CPU, and generally we have a tight window we are aiming for with Latency. This means that it just isn't possible to exhaustively score every document on every query.

## Pruning
only consider documents containing at least N parts of the query
## Efficient
**Safe Ranking** is when the methods guarantee that the k-docs that are returned are the K absolute highest scoring documents, however if most scenarios like web search it is ok to be non-safe.

To do this we want to find the K docs in the collection "nearest" to the query, which is the K-nearest neighbor problem. Generally this suffers from the curse of dimensionality, making it hard. To simplify our problem we assume no weighting on query terms, assuming each appears once, and then we don't normalize the query. This helps but not too much.

**Trimming**
Since the main bottleneck is the cosine computation we need to find a way to reduce the number of documents to score. We can do this by finding a set A of contenders, with $K < |A| < N$ where A may not contain the top document but it does contain a number of the best documents. The bottom line is to only consider docs that are containing at least one query term, but we can take this further by only considering high-idf query terms, docs with many query terms, or only top docs for each query term.

## Query Independent

**Cluster Pruning**
Pick $\sqrt N$ docs at random (though in practice we can do better than random), and we call these documents the leaders. Then we just do our query similarity on the leaders and the documents closest to the leaders. This can run into problems if the query is in-between two clusters.

**Tiered Indexes:**
We break postings up into a series of ranked lists, and then we can go in order from tier-one documents to tier 2 etc as needed.
# References
- [[Vector Space Model]]
- [[K nearest Neighbors (kNN)]]

