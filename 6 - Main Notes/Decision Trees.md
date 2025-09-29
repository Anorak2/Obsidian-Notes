
2025-09-02

Tags: [[EECS 568 - Intro to Data Mining]] 
# Decision Trees
![[Pasted image 20250902144740.png]]
Fig 1. An example of a decision tree

Decision trees have a flow chart sort of tree structure where each internal node (yellow in example) tests one attribute and each branch from a node selects on attribute. Each lead node (blue in example) as a prediction for the label y. 

**Advantages**
* Inexpensive to construct
* Extremely fast at classifying unknown records
* Easy to interpret for the small-sized trees
* Robust to noise
* Can easily handle redundant or irrelevant attributes

**Disadvantages**
* Due to the greedy nature of splitting, attributes that interact may be passed over for other attributes that are less discriminating. For a simplified example, credit score and income may be the sole determiners of if someone can buy a house. It may be very relevant to the dataset to see if someone can buy a house, but unless the creator includes that the decision tree won't be able to act on that derived record.
* Each decision boundary involves only a single attribute
# References
[[Splitting on Decision Trees]]
