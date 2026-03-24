
2025-11-13

Tags: [[Data Mining and Machine Learning]]
# Strong Learners (Ensemble Methods)
## Base
Strong learners are a combination of multiple different, weaker, models. The idea is that all of these models are based on the objective picture, but each has a certain number of errors.  However, if these errors are uncorrelated when we average these weaker models together we tend to get a model with higher accuracy since they fill each-others weaknesses.

If all classifiers are independent trained
- Errors are uncorrelated - each classifier has error on different data points
- Error rate of ensemble = probability of having more than half of classifiers being wrong

$$e_{ensemble}=\sum^{25}_{i=13}{25 \choose i}e^i(1-\epsilon)^{25-i}=.06$$
**Pros:**
- Improved Accuracy
- Less susceptible to noise (more robust)
- Reduced over fitting

**Cons:**
- Increased computational cost
- Increased complexity
- Diminishing Returns

## Generating Base Learners
### One-vs-Rest Strategy
Splits a multi-class classification into one binary classification problem per class, with K classes $C_1,\space C_2,\space ..., C_k$. Then you train K models with each model trying to predict simply is it in class $C_n$ or is it not in class $!C_n$. This approach only works when you have a model that returns a value in \[0,1\] determining which class, an example is a neural network. Whichever model has the highest degree of confidence is the output the ensemble model chooses.

### One-vs-One Strategy
If we have three classes, say (A, B, C), then this approach splits it into a series of 1v1's so that means a model trained on (A, B), another on (B, C) etc.

The fusion might look like
Model 1: A and B $= 0.3  \to p_1(A) = 0.3 \text{ and } p_1(B) = 0.7$
Model 2: A and C $= 0.6 \to  p_2(A) = 0.6 \text{ and } p_2(C) = 0.4$
Model 3: B and C $= 0.8 \to p_3(B) = 0.8 \text{ and } p_3(C) = 0.2$
$p(A) = p_1(A) \cdot p_2(A) = 0.3·0.6 = 0.18$
$p(B) = p_1(B) \cdot p_3(B) = 0.7·0.8 = 0.56$
$p(C) = p_2(C)\cdot p_3(C) = 0.4·0.2 = 0.08$
B is selected as the class because $p(B)$ is the largest
### Bagging
Bootstrap Aggregating (Bagging) is an approach similar to voting, but it trains the individual learners on a slightly different set of data rather than training each on the same dataset. Bootstrap in this context is when each individual learner draws a sample from the training data (with replacement) and then fusing the output later. Typically bagging is implemented with Decision Tree models and with Neural Network models since these models are unstable, amplifying the impact of bagging.

## Fusion Methods
### Voting - Categorical Fusion
The class output is decided by democracy where we fuse the "opinions" of each of the classifiers. **Hard Voting** is where we count the total number of votes for + and -, where **Soft Voting** is where classifiers more "sure" will vote with more conviction. In soft voting we sum up the probabilities for +/-. 
### Value Fusion
Mean:
In this version take a weighted average of the outputs, with the weight determining how much we value the output of a model.

Median:
As you would expect

## In Python

- [One-vs-Rest](https://scikit-learn.org/stable/modules/generated/sklearn.multiclass.OneVsRestClassifier.html#sklearn.multiclass.OneVsRestClassifier)
- [One-vs-One](https://scikit-learn.org/stable/modules/generated/sklearn.multiclass.OneVsOneClassifier.html#sklearn.multiclass.OneVsOneClassifier)
-  [Voting Classifier](https://scikit- learn.org/stable/modules/ensemble.html#voting-classifier).  It supports Voting, Weighted Average, Mean (use Weighted Average with all the weights equal)
- [Bagging Classifier](https://scikit- learn.org/stable/modules/generated/sklearn.ense mble.BaggingClassifier.html?highlight=bagging#skl earn.ensemble.BaggingClassifier)

# References
- [[Logistic Regression]]
- [[Decision Trees]]
- [[Neural Networks]]
- [[Discriminate Analysis Quantifiers]]
- [[Random Forest]]
- [[Neural Networks]]