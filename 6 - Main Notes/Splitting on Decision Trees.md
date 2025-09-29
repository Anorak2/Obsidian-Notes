
2025-09-11

Tags: [[EECS 568 - Intro to Data Mining]]
# Splitting on Decision Trees
 **Finding the best attribute for a split**

1. Computer impurity measure (P) before splitting
2. Compute impurity measure (M)  after splitting
	1.  Computer Impurity measure of each child node
	2. M is the weighted average of child nodes' impurity
3. Choose the attribute test condition that produces the highest gain where $Gain = P - M$ 

## Gain
Gain of an attribute split into children: Compare the impurity of the parent node with the average impurity of the child nodes
$$Gain = i(parent) - \sum^k_{j=1} \frac{N(child)}{N}I(child_j)$$
Maximize the gain, minimize the weighted average impurity of children nodes and maximize purity.

**Computing Gain after splitting**
$$Gain_{split}=Entropy(p)-\sum^k_{i=1}\frac{n_i}{n}Entropy(i)$$
where the parent node p is split into k partitions, $n_i$ is the number of records in the child node i
## Gini Index
The Gini Index is a measure of impurity, and for a given node t it can be calculated as:
$$\text{Gini Index}= 1 - \sum_{i=0}^{c-1} p_i(t)^2$$
Where $p_i(t)$ is the frequency of class i at node t, and c is the total number of classes

- Maximum of 1 - 1/c when records are equally distributed among all classes, implying the least beneficial situation for classification 
- Minimum of 0 when all records belong to one class, implying the most beneficial situation for classification

**Computing Gini Index for a collection of nodes**
$$GINI_{split} = \sum^k_{i=1} \frac{n_i}{n}GINI(i)$$
## Entropy
Entropy is another way we can measure impurity, and it can be calculated at a given node t by:
$$Entropy = - \sum^{c-1}_{t=0} p_i(t)\log_2p_i(t)$$
Where $p_i(t)$ is the frequency of class i at the node t, and C is the total number of classes
- Maximum of $\log_2 c$ when records are equally distributed among all classes
- Minimum of 0 when all records belong to one class
It is actually pretty similar to the Gini index computations


## Continuous Attributes: 
Where do we split on a continuous scale? 50k, 100k, 1 million?
- Use binary decisions based on one value
- Several choices for the splitting value
	- Number of possible splitting values == the number of distinct values
- Each splitting value has a count matrix associated with it
	- Class counts in each of the partitions, A $\leq$ b

**for efficient computation**
- Sort the attribute on values
- Scan the values, each time update the count matrix and compute Gini index
- Choose the split position that has the smallest Gini index

## Gain Ratio (Reducing number of partitions)
One of the problems with all of the previous techniques is that they want to create a very high amount of small but very pure partitions, but this is unoptimal because it overfits to our data. To solve this we can use the gain ratio to adjust the information gain by the entropy of the partitioning, and this is good since it penalizes a large number of small partitions
$$\text{Gain ratio} = \frac{Gain_{split}}{Split_{info}} $$
$$\text{Split Info} = - \sum^k_{t=1} \frac{n_i}{n}\log_2\frac{n_i}{n}$$
Parent node $p$ is split into $k$ partitions (children)
$n_i$ is the number of records in child node i

## Misclassifcation Error
The classification error at a node *t*
$$Error(t)=1-\max_i[p_i(t)]$$
This assigns the class with the most data as the prediction for the entire node. It has a **Maximum** of 1-1/c when records are equally distributed among all classes, implying the least interesting situation. Minimum of 0 when all records belong to one class, implying the most interesting situation.
# References

