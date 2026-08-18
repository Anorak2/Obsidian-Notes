
2026-03-04

Tags: [[Data Mining and Machine Learning]]
# Simulated Annealing (Feature Selection)
Simulated annealing is another approach that attempts to find a global optimum when brute force is too inefficient.
## Algorithm
The Simulated Annealing (SA) feature selection algorithm begins with the original d features as the subset. The number of iterations is arbitrary, but a good number is 100.
![[Pasted image 20260304223910.png]]
**Perturb the feature set**
A small percentage (1-5%) of features are randomly added or deleted from the current feature set.

**Fit Model**
Use k-fold cross-validation to train the ML model and then estimate the performance with the Accuracy metric.

**Acceptance Probability**
If the Accuracy is worse than the previous subset, then calculate the acceptance probability:
$$Pr[accept]=e^{-\frac{i}{c}(\frac{old-new}{new})}$$
where
i = current number of iterations
c = constant (default is 1)
old = old Accuracy
new = new Accuracy

**Reject/Accept worse Subset**
This code has a tendency to accept new Accuracy values that are less than the old Accuracy values early in the process. This has a tendency to make the algorithm “jump” to the next valley instead of staying in the current one. Thus, it overcomes the tendency of a “greedy” algorithm to find the first valley.

**Restarts**
The random nature of the search and the acceptance probability criteria help the algorithm avoid local optimums. But, a modification called restarts provides an additional layer of protection from lingering in inauspicious locales. If a new optimal solution has not been found within x iterations, then the search resets to the last known optimal solution and proceeds again with i being the number of iterations since the restart.
# References
- [[Dimensionality Reduction]]

