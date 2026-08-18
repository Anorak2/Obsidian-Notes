
2026-02-23

Tags: [[Data Mining and Machine Learning]]
# Dimensionality Reduction
In most of my notes with supervised models we use all of the features, but dimensionality reduction is the practice of compressing information from multiple features down. There's a few reasons we want to do this, namely the curse of dimensionality, reducing space complexity, improves accuracy, and saves the cost of observing the feature. From a high level we do this by eliminating redundant features, eliminating features that don't really matter, and by eliminating features that cancel other features out.

## Brute Force
The optimum set of features to select could be determined by brute-force, i.e., or an exhaustive search. In an exhaustive search, each combination of features is tried to find the optimum subset of features to use. Assuming each iteration (training and testing of the data) takes 0.1 sec:
- 4 features would take: 1.5 seconds
- 10 features would take: 102.3 seconds
- 15 features would take: 0.9 hours
- 20 features would take: 1.2 days
- 25 features would take: 39 days
- 30 features would take: 3.4 years
## Sub-Optimum Feature Selection 
When we cannot use a brute-force algorithm to find the optimum feature subset, we use a sub-optimum feature selection algorithm that tries to come close to the optimum solution.

### Greedy Algorithms
A greedy algorithm is a problem-solving approach that makes the locally optimal choice at each step, aiming to find a global optimum. By only selecting for the immediate option they often fail to be optimal in the long run but they are fast.
[[Sequential Search (Feature Selection)]]

# References
- [[Supervised Learning*]]
- [[Principle Component Analysis (PCA) (feature transform)]]
