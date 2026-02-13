
2026-02-06

Tags: [[Data Mining and Machine Learning]]
# Random Forest
## Random Forest
Random forest is a technique to help mitigate some of the weaknesses of decision trees. These weaknesses include a tendency to over-fitting, instability due to small variations in data, and training can't guarantee globally optimal decision trees. Fortunately we can mitigate these using the random forest technique.

We instead create a **forest** of multiple decision trees with each producing different classifications, and a majority vote is used to select the final output.
![[Pasted image 20260206211816.png]]

Typically a few hundred to several thousand trees are used since they are relatively very cheap, and to ensure they are different each tree has a random subset of training data and a random subset of features.

## Extremely Randomized Trees (Extra Trees)
Adding one further step of randomization gives us extremely randomized trees, or ExtraTrees. Similarly with random forests, a random subset of candidate features is used, but instead of looking for the most discriminative thresholds during training, thresholds are drawn at random for each candidate feature and the best of these randomly-generated thresholds is picked as the splitting rule.

# References
- [[Decision Trees]]
- [[Strong Learners]]