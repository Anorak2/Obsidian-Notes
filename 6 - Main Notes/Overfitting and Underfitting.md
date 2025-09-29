
2025-09-11

Tags: [[Data Mining Lecture]]
# Overfitting and Underfitting
![[Pasted image 20250911003704.png]]

**Underfitting** is when the model is too simple, and both the training and test values have large amounts of errors

**Overfitting** is when the model is too complex and it models the details of the training set too closely, and as a result it fails on the test set. In decision trees over fitting results in trees that are much more complicated then necessary. Training error also loses it's value as a good estimate of test error.

**Generalization:** This is a models ability to predict data points that it has not already seen, and often our goal is to improve this exact value.


## Addressing Overfitting
**Pre Pruning** is when you stop the algorithm before it becomes a fully grown tree, typically when all instances belong to the same class or all attribute values are the same. There are also more restrictive conditions like a hard set amount on the number of instances, stopping expanding the current node doesn't improve impurity measures, and stop if the generalization error falls below some threshold. 

**Validation Set** is when we have a holdout part of the training set to provide an unbiased evaluation of a model on the training dataset.


**Post Pruning** is when we grow the decision tree to its entirety and then trim the nodes of the decision tree in a bottom up manner. If the generalization error improves after trimming then replace the sub-tree with a leaf node.
# References
[[Decision Trees]]