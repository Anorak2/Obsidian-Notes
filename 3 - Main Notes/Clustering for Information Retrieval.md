
2026-04-06

Tags: [[Information Retrieval]] [[Data Mining and Machine Learning]]
# Clustering for IR
As a review, we don't always have labelled data which is where unsupervised methods come into play with clustering as the primary unsupervised model.

**Applications**
- Whole corpus analysis/navigation as a way to limit typing / requerying
- For improving recall in applications due to better search results (like pseudo RF).
- For better navigation of search results, effective “user recall” will be higher
- For speeding up vector space retrieval 


**Hard clustering** is when each document belongs to exactly one cluster, this is more common and easier to do.

**Soft clustering** is when a document can belong to more than one cluster. This makes more sense for applications like creating browsable hierarchies. For example You may want to put a pair of sneakers in two clusters: (i) sports apparel and (ii) shoes. You can only do that with a soft clustering approach.

## Purity
Clustering Quality measured by its ability to discover some or all of the hidden patterns or latent classes in gold standard data. Assesses a clustering with respect to ground truth … requires labeled data. Assume documents with C gold standard classes, while our clustering algorithms produce K clusters, ω1, ω2, …, ω K with n_i members.
$$\text{Purity}(\omega_i) = \frac{1}{n_i} \max \space(n_{ij}), \space \space {j \in C}$$
# References
- [[Clustering and Clustering Analysis*]]
- [[K-means Clustering]]
- [[Hierarchical Clustering]]
