
2025-09-02

Tags: [[Data Mining and Machine Learning]] 
# Decision Trees
![[Pasted image 20250902144740.png]]
Fig 1. An example of a decision tree

Decision trees have a flow chart sort of tree structure where each internal node (yellow in example) tests one attribute and each branch from a node selects on attribute. Each lead node (blue in example) as a prediction for the label y. 

**Advantages**
* Inexpensive to construct
* Extremely fast at classifying unknown records
* Easy to interpret for the small-sized trees, especially because they can be visualized
* Robust to noise
* Can easily handle redundant or irrelevant attributes
* We can validate it using statistical tests
* Performs well even if its assumptions are somewhat violated by the true model from which the data were generated.
- They are good at predicting classes when the boundaries between classes are non-linear.
- non-probabilistic

**Disadvantages**
* Due to the greedy nature of splitting, attributes that interact may be passed over for other attributes that are less discriminating. For a simplified example, credit score and income may be the sole determiners of if someone can buy a house. It may be very relevant to the dataset to see if someone can buy a house, but unless the creator includes that the decision tree won't be able to act on that derived record.
* Each decision boundary involves only a single attribute
* tend to overfit
* they can be unstable
* learning a purely optimal decision tree is an NP hard problem
* decision trees can easily be biased 

## Practical
Decision trees in python:
```Python
# Import the library
from sklearn import tree
# To train the model:
clf = tree.DecisionTreeClassifier()
clf = clf.fit(Training_Features, Training_Classes)
# To predict classes from the model:
clf.predict(Test_Classes)
# You can also print out the decision tree using the plot_tree function:
from sklearn.datasets import load_iris
from sklearn import tree
X, y = load_iris(return_X_y=True)
clf = tree.DecisionTreeClassifier()
clf = clf.fit(X, y)
tree.plot_tree(clf.fit(iris.data, iris.target))
```

Random Forest in python:
``` Python
# To import the library:
from sklearn.ensemble import RandomForestClassifier
# To train the model:
clf = RandomForestClassifier()
clf = clf.fit(Training_Features, Training_Classes)
# To predict classes from the model:
clf.predict(Test_Classes)
```

Extra Trees in python:
```Python
# To import the library:
from sklearn.ensemble import ExtraTreesClassifier
# To train the model:
clf = ExtraTreesClassifier()
clf = clf.fit(Training_Features, Training_Classes)
# To predict classes from the model:
clf.predict(Test_Classes)
```

# References
[[Splitting on Decision Trees]]
