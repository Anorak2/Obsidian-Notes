
2025-12-10

Tags: [[Data Mining]] [[Data]] [[Algorithms]]
# DBSCAN
DBSCAN is a Density-Based Clustering algorithm, In density based clustering we partition points into dense regions separated by not-so-dense regions. With DBSCAN the two main questions are how do we measure density, and what is a dense region.

DBSCAN
- Density at point p: number of points within a circle of radius `Eps`
- Dense Region: a circle of radius `Eps` that contains at least `MinPts` points

#### Points Labels:
- A point is a **core point** if it has more than a specified number of points (`MinPts`) within radius `Eps`, these points belong in a dense region and are at the interior of a cluster
- A **border point** has fewer than `MinPts` within `Eps`, but is in the neighborhood of a core point.
- A **noise point** is any point that is not a core point or a border point.

#### DBSCAN Algorithm 
1. Label all points as core, border, or noise points.
2. Eliminate noise points.
3. Put an edge between all core points within a distance `Eps` of each other.
4. Make each group of density-connected core points into a separate cluster.
5. Assign each border point to one of the clusters of its associated core points

#### Setting `EPS` and `MinPts`
- Idea is that for points in a cluster, their k'th nearest neighbors are at close distance
- Noise points have the k'th nearest neighbor at farther distance
- So, plot sorted distance of every point to its k'th nearest neighbor, use “sharp change” of curve as `Eps`
![[Pasted image 20251210233144.png]]


#### Pro / Cons
- DBSCAN is resistant to noise
- DBSCAN can handle a variety of shapes and sizes 
- DBSCAN struggles with varying densities and when one radius `Eps` doesn’t fit all densities
- DBSCAN also struggles with high dimensional data since it is harder to define density and the cost increases

#### Complexity
- Time: $O(n\log n)$ with worst case $O(n^2)$
- Space: $O(n)$ – only need to store point label

# References
[[Clustering and Clustering Analysis]]

[[K-means Clustering]]

[[Hierarchical Clustering]]