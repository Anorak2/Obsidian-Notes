
2025-12-10

Tags: [[Data Mining and Machine Learning]]
# Discriminate Analysis Quantifiers 

## Practical
---
**Benefits:**
	These classifiers are attractive because they have closed-form solutions that can be easily computed, are inherently multiclass, have proven to work well in practice, and have no hyper-parameters to tune.

Both LDA and QDA can be derived from simple probabilistic models which model the class conditional distribution of the data $P(X|y=k)$ for each class k.

Predictions can then be made by using Bayes' rule, and we select the K class that maximizes this conditional probability.
![[Pasted image 20260201171013.png]]

For quadratic discriminant analysis P(X | y) is a multi-variable gaussian distribution, with a density function:
![[Pasted image 20260201171351.png]]
where d is the number of features

![[Pasted image 20260201171613.png]]

## Varieties
The formulas for the LDA/QDA are actually remarkably similar to the naive bayes classifier, this is actually because the naive bayes classifier is a simplification of the LDA where features are assumed to be independent of one another.
Thus
- Naive Bayesian - no covariance
- LDA - covariance is the same for all classes
- QDA - covariance is different for each class
# References
- [[Bayes Theorem]]
- [[Gaussian (normal) CRV]]
- [[Naive Bayes Classifier]]