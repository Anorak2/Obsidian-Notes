
2025-12-10

Tags: [[Data Mining]] [[Data]] [[Algorithms]]
# Hierarchical Clustering
This form of clustering Produces a set of nested clusters organized as a hierarchical tree. It can be visualized in a few ways, as a dendrogram, a tree like diagram that records the sequences of merges or splits, or the X-axis: data points, Y-axis: distance between clusters.
![[Pasted image 20251210225138.png]]
**Strengths:**
- Do not have to assume any particular number of clusters
	- Any desired number of clusters can be obtained by ‘cutting’ the dendrogram at the proper level
- Dendrograms may correspond to meaningful taxonomies
	- Example in biological sciences (e.g., animal kingdom, phylogeny reconstruction, …)

**Types:**
- Agglomerative:
	- Start with the points as individual clusters
	- At each step, merge the closest pair of clusters until only one cluster (or k clusters) left
- Divisive:
	- Start with one, all-inclusive cluster
	- At each step, split a cluster until each cluster contains an individual point (or there are k clusters
#### Agglomerative Algorithm:
Key operation is the computation of the proximity of two clusters, different approaches to defining the distance between clusters distinguish the different algorithms

1. Compute the proximity matrix
2. Let each data point be a cluster
3. Repeat:
	1. Merge the two closest clusters
	2. Update the proximity matrix
4. Until only a single cluster remains

## Inter-Cluster Distances
Several different approaches:
- MIN (single link)
	- Min is capable of handling rather complex shapes but it is sensitive to noise
- MAX (complete link)
	- Max is much better at handling noise and outliers than min but it tends to break large clusters and it is biased towards globular clusters
- Group Average
	- This is a compromise between Min and Max, it combines their strengths by being less susceptible to noise but it is still biased towards globular clusters
- Distance between Centroids
- Others driven by an objective function
	- Ward's Method uses squared error
	- Distance of two clusters is based on the increase in squared error (SSE) when two clusters are merged
		- Similar to group average if distance between points is distance squared
	- Less susceptible to noise and outliers but it's still biased towards globular clusters
	- Hierarchical analogue of K-means, and it can be used to initialize K-means
![[Pasted image 20251210225613.png]]
![[Pasted image 20251210230023.png]]
## Formal Pros and Cons
---
- O($N^2$) space, where there are N points, since it uses the proximity matrix.
- O($N^3$) time in many cases
	- There are N steps and at each step the size, N2, proximity matrix must be updated and searched
	- Complexity can be reduced to O(N2 log(N) ) time with some cleverness

**Limitations:**
- Computational complexity in time and space
- Once a decision is made to combine two clusters, it cannot be undone
- No global objective function is directly minimized
- Different schemes have problems with one or more of the following:
	- Sensitivity to noise
	- Difficulty handling clusters of different sizes and non-globular shapes
	- Breaking large clusters
# References
[[Clustering and Clustering Analysis]]

[[K-means Clustering]]