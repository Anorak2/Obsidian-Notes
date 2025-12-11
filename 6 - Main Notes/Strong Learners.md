
2025-11-13

Tags:
# Strong Learners
![[Pasted image 20251113141901.png]]
Strong learners aren't anything particularly novel, instead a strong learner is the combination of several other weak learners that are combined to form a stronger classifier.

#### Voting
The class output is decided by democracy where we combine the "opinions" of each of the classifiers. **Hard Voting** is where we count the total number of votes for + and -, where **Soft Voting** is where classifiers more "sure" will vote with more conviction. In soft voting we sum up the probabilities for +/-. 

#### Why does ensemble work?
 Suppose there are 25 weak classifiers where each classifier has error rate $\epsilon$ = 0.35, hard voting is used by counting majority.
 
  If all classifiers are independent trained
- Errors are uncorrelated - each classifier has error on different data points
- Error rate of ensemble = probability of having more than half of classifiers being wrong

$$e_{ensemble}=\sum^{25}_{i=13}{25 \choose i}e^i(1-\epsilon)^{25-i}=.06$$



# References
[[Logistic Regression]]

[[Decision Tree]]

[[Support Vector Machines (SVM) *]]