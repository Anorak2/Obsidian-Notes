
2025-08-26

Tags: [[EECS 568 - Intro to Data Mining]] [[Data]]
# Data Pre-processing

**Aggregation**
> Combining two or more data objects into a single object. We do this because it can be easier to work with and so that we can have more stable data

## Sampling
> Sampling is used when computation is expensive so that instead of working with potentially billions of values we can choose an amount small enough to be easily worked with. The key principles are that sampling will work almost as well as using the entire set if the sample is representative and that a sample is representative if it has approximately the same property of interest as the original set.

Warning: Be careful with sample sizes, there is no one size fits all but structures can easily be erased in low resolutions caused by small samples

## Curse of Dimensionality
> Many types of analysis are much harder as the dimensionality of the data increases, part of this is because as the dimensions increase the data becomes increasingly sparse in the area that it occupies. As dimensions grow it also becomes harder to visualize and manipulate data, so it is very important to choose the most informative features in the data set to make it easy.

One common goal with data mining is trying to find a projection that captures the largest amount of variation in a data set so that it is easier to work with. This is generally effective but it can be problematic since projections can distort the information.

## Feature Subset Selection

## Feature Creation


# References

