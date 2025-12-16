
2025-12-10

Tags: [[Data Mining]] [[Data]] [[Algorithms]]
# K-means Clustering
## Algorithm
---
Partitional clustering approach:
- Each cluster is associated with a centroid (center point)
- Each point is assigned to the cluster with the closest centroid
- Number of clusters, K, must be specified
- Objective
	- Find K centroids and assign every data points a centroids
	- Minimize the sum of distances of all the points to their respective centroid

Complexity is O( n * K * I * d )
- n = number of points
- K = number of clusters
- I = number of iterations
- d = number of attributes
![[Pasted image 20251210212456.png]]

Ex:
![[Pasted image 20251210212520.png]]
## Objective Functions
---
The Sum of Squared Error, or SSE, is a common objective function used with the euclidean distance measure.  For each point, the error is the distance to the nearest cluster center (centroid), to get SSE, we square these errors and sum them.
$$SSE=\sum^K_{i=1}\sum_{x \in C_i}(x-c_i)^2$$
- 𝐾 is number of clusters
- 𝑥 is a data point in cluster $C_i$
- $c_i$ is the centroid (mean) for cluster $C_i$
- SSE improves in each iteration of K-means until it reaches a minima

## Initialization 
---
When we choose the starting point it actually is very significant where our starting points are, this isn't good since we want to deterministically find the best clusters. To deal with initialization we do multiple runs and select the run with the smallest error, though we can also select points in a non-random way(k-means++).

## K-means++
![[Pasted image 20251210223454.png]]
![[Pasted image 20251210223429.png]]
## Bisecting K-means
Variant of K-means that can produce a partitional or a hierarchical clustering
![[Pasted image 20251210223544.png]]

## Limitations:
K-means has problems when clusters are of differing
- Sizes
- Densities
- Non-globular shapes
K-means has problems when the data contains outliers.
- One possible solution is to remove outliers before clustering

# References
[[Clustering and Clustering Analysis]]

