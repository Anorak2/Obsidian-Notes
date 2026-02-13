
2026-01-23

Tags: [[Data Mining and Machine Learning]]
# Naive Bayes Classifier
The Naive Bayes Classifier is the simplest machine learning classifier, and it is used as a "gold standard" for comparing machine learning models.
## Naive Bayes Classifier
The Naïve Bayesian classifier is a conditional probability model. A sample to be classified is represented by a vector $x = (x_1, x_2, … x_n)$ of n feature values. It calculates the conditional probabilities for the sample $p(C_i|x_1, x_2, ... x_n)$ for each possible class $C_i$. The problem with this is that calculating every probability can be computationally impossible.
Generally the equation can be described as
$$\text{posterior}=\frac{\text{prior}\cdot\text{likelihood}}{\text{evidence}}$$
Practically we only care about the numerator because the denominator doesn't depend on $C_i$ 

$$\text{posterior numerator}=\text{prior}\cdot\text{likelihood}$$
and we classify by the largest posterior numerator

**Summary:**
- Calculate one probability (P) for each class
- calculate $n \cdot m$ conditional probabilities (p) where
	- n = number of classes
	- m = number of features

**Strengths**
- Simple to train

**Weaknesses**
- Assumes a Gaussian distribution, which isn't always the case
- Assumes features are independent
- Based on probability theory, which is find but can be oversimplified compared to real world scenarios


# References
- [[Bayes Theorem]]
- [[Discriminant Analysis Classifiers]]
