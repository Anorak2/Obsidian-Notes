
2025-12-10

Tags: [[Data]] [[Data Mining]]
# Clustering and Clustering Analysis
**Definition:** Given a set of objects, grouping them such that the objects in the same group (cluster) are similar (or related) to one another and that the objects are different from (or unrelated to) the objects in other groups. We try to minimize the distance between points in a cluster and maximize the distances between clusters. Clustering is also **subjective**, someone may choose to cluster by gender, job, age, etc. The notion of a cluster can also be very ambiguous.

## Clustering Distinctions
---
- Exclusive (or non-overlapping) vs. non-exclusive (overlapping)
	- In non-exclusive clustering, points may belong to multiple clusters.
- Fuzzy (or soft) clustering vs. non-fuzzy (or hard)
	- In fuzzy clustering, a point belongs to every cluster with some weight (or probability) between 0 and 1
	- Weights must sum to 1
- Partial vs. complete
	- In some cases, we only want to cluster some of the data
## Types of Clusters
---
- Well Separated: 
	- A cluster is a set of points such that any point in a cluster is closer (or more similar) to every other point in the cluster than to any point not in the cluster. 
- Prototype-based (or center-based) clusters
	- A cluster is a set of objects such that object of a cluster is closer (more similar) to the prototype (center) of a cluster, than to the center of other clusters
	- Centroid, the average of all the points in the cluster
	- Medoid, the most “representative” point of a cluster
- Contiguous cluster (nearest neighbor or transitive)
	- A cluster is a set of points such that a point in a cluster is closer (or more similar) to at least one points in the cluster than to any point not in the cluster.
- Density-based clusters
	- A cluster is a dense region of points, which is separated by low-density regions, from other regions of high density.
	- Used when the clusters are irregular or intertwined, and when noise and outliers are present

## Cluster Evaluation
---
**Why and How?** 

#### Unsupervised Measures

#### Supervised Measures

#### Correlation
# References
[[K-means Clustering]]

[[Hierarchical Clustering]]

[[DBSCAN]]
