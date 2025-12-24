
2025-12-16

Tags: [[Data Mining]]
# Boosting + AdaBoost
An iterative procedure to adaptively change distribution of training data by focusing more on previously misclassified records
- Initially, all N training instances are assigned equal weights
- Wrongly classified will have their weights increased in the next round
- Correctly classified will have their weights decreased in the next round
- On each iteration 𝑡
	- Weight each training instance by how incorrectly it was classified
	- Learn a weak model - ℎ𝑡
	- A strength showing importance of model at current iteration - 𝛽𝑡

![[Pasted image 20251216003705.png]]

## AdaBoost
![[Pasted image 20251216003811.png]]
![[Pasted image 20251216003856.png]]

This works because the final decisions are voting with the importance of each learner. We do this by starting with each point of equal weight, and to weight each point we can simply just incorporate the weights into the cost function (line 3). Line 4 is the error: the sum of the weights of all misclassified instances. $\beta_t$ measures the importance of $h_t$ and as $\beta_t$ grows the error of $h_t$ shrinks (line 5). Emphasize the misclassified instances by increase their weights (line 6). Member classifiers with less error are given more weight in the final ensemble model (line 9). Final prediction is a weighted combination of each member’s prediction

**Summary:**
Strengths:
- Fast and simple to program
- No parameters to tune
- No assumptions on weak learner

When boosting can fail
- Given insufficient data
- Overly complex weak model
- Can be susceptible to noise
- When there are a large number of outliers
# References
[[Strong Learners]]