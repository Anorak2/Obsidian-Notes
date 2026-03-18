
2026-03-11

Tags: [[Data Mining and Machine Learning]]
# Dealing with Imbalanced Datasets
Often when we are in school we deal with idealized datasets like the Iris dataset with exactly 50 of each class. In practice this is very difficult, for example if you are developing self driving cars you likely don't have a lot of samples of kids running out into the street. The three main approaches to fixing an imbalanced dataset are to collect more data, change the performance metric, and oversampling and under sampling.

### Collect More Data
This is the simplest but also by far the best solution. It's important not to just gather data as usual but to focus on underrepresented classes. Even if you can't balance the classes you will have a better data set for under sampling / over sampling.
### Change the Performance Metric
When you are working with an imbalanced dataset you can no longer use accuracy as  a metric. If you did, then a model would be able to just ignore the few other cases and still "perform" well. There isn't a consensus on what is best to use, but the following ones are common.

Class Balanced Accuracy
1. Calculate the precision (P) and the recall (R) for each class.
2. Find the minimum between the precision (P) and the recall (R) for each class.
3. Average these minimums over all the classes to get the Class Balanced Accuracy.

Balanced Accuracy
1. Calculate the recall (R) and specificity (S) for each class.
2. Average the recall (R) and specificity (S) for each class.
3. Average these averages over all the classes to get the Balanced Accuracy.

### Under Sampling / Over Sampling
![[Pasted image 20260312003221.png]]
The idea is to copy data until the imbalance can be made up. Generally oversampling is used over under-sampling since we worked hard to collect that data and it sucks to throw it aside. In 658 we cover three popular techniques, Random Oversampling, Synthetic Minority Over-sampling Technique (`SMOTE`), Adaptive Synthetic Sampling Approach (`ADASYN`). `imbalanced-toolbox` is a library that we can use to implement all of these techniques, [documentation](https://imbalanced-learn.org/stable/references/index.html).

**Random Oversampling:**
This is one of the earliest and one of the most robust methods. The idea is to supplement the training data with multiple copies of some of the minority classes, and this can be done multiple times. Instead of duplicating every sample in the minority class, some of them may be randomly chosen with replacement. This is exactly like pulling a colored marble from a bag and then replacing it after pulling it.

**SMOTE Oversampling:**
![[Pasted image 20260312004046.png]]
This approach doesn't seem ideal, but it works by synthesizing new data points. You take a sample in a N vector space and then draw a line to each one of it's K nearest neighbors and place a new point somewhere along each line. There have been a number of modifications and proposals to SMOTE since it's creation, but they all work by filling out the "cloud" of points in that same way.

**`ADASYN` Oversampling:**
This is another method for synthesizing data in a way that is very similar to SMOTE. In the same way we create vectors to each of the K nearest points, but rather than pointing to each of K `ADASYN` will only add a new point within a cutoff distance. To determine which and how many of the closest neighbors, ADASYN uses a density distribution function to determine which and how many of the closest neighbors to use.

**Under Sampling:**
As the name implies, this method randomly removes samples from the majority class without replacement. The problem is that we may increase the variance of the classifier due to fewer samples, and we may potentially discard useful or important samples.
# References
- 