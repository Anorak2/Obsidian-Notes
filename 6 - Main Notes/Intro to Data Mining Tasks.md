
2025-08-21

Tags: [[Data Mining]] [[Data]]
## Models
> Models are a way to represent our predictions about what will happen in the future based on what has been predicted to be statistically likely so that we can infer results.

## Classification
as long as our goal is to make some kind of future prediction based on info then we are doing classification work.

**Classification techniques:**
Base Classifiers:
- Decision Tree based methods
- rule based methods
- nearest neighbor
- neural networks
- Naive Bayes and Bayesian Belief Networks
- Support Vector Machines

Ensemble Classifiers
- Boosting, Bagging, Random Forests

**Regression** Predict a value of a given continuous variable based on the values of other variables, and assume either a linear or nonlinear dependency model. These have been extensively studied and have use cases such as predicting sales amounts of a new product based on amount of advertising spending.

## Clustering:
> This is where we find groups of objects such that the objects in a group will be similar (or related) to one another and different from (or unrelated to) the objects in other groups. The goal of clustering is not for prediction, it's to understand.

Clustering can be useful for gaining a rough understanding a group, like how proteins work, and very good for gaining a quick understanding of a dataset and if there are meaningfully separated categories. One of the downsides though is that the notion of a cluster can be ambiguous, and two engineers might count different numbers of groups on the same data.

## Association 
> Association is where given a set of records each of which contains some items from a given collection, produce dependency rules which will predict occurrence of an item based on occurrences of other items.

Association has some useful applications, one example is that given a combination of patient symptoms and complaints we can associate these with certain diseases in very nuanced ways.

## Anomaly Detection
> Anomaly detection means detecting significant deviations from normal behavior, common examples include credit card fraud detection and network intrusion detection.

Usually 99.9% of the data is considered normal and to create a classification model we need to detect those 0.1% of cases which can be tricky due to data limitations. Ex: credit card fraud happens but for the average user not that frequently, maybe every few years on average. 

## KDD Process
- Select a data mining task; Classification,
- Select data mining approach
- Data mining to extract patterns or modules
- Data mining to discover patterns
- Interpretation / Knowledge

# References

