
2026-02-01

Tags: [[Data Mining and Machine Learning]]
# K nearest Neighbors (kNN)
The model representation for kNN is the simply the entire training dataset, and that's it. There really is no learning required at all, though there are fancy data structures that allow for lookup and matching to be more efficient for predictions. By the nature of kNN it is very easy to add more data or remove bad data at a whim since there is no retraining cost. The drawback is that we have no compression so the model is quite large.

**Predictions** are made by searching the entire dataset for the k most similar instances (neighbors), and then finding the mode class value. The most common distance measure is simply euclidean distance, though others exist.

**Choosing K** is a very important part of making a model since a very small K, such as 1, leads to over-fitting. Yet a very large K leads to under-fitting where all useful details are smoothed out. A quick starting point is to set k equal to the **square root** of the number of training samples  ($k = \sqrt n$). You can also use the elbow method, where you plot the Accuracy on the Y-axis and k on the X-axis. Look for the point where the Accuracy significantly increases and then begins to level off. This "**elbow**" represents a good balance between complexity and error.

**Strengths**:
- Simple – the model is the training data.
- Easy to update
- It makes no assumptions about the distribution or independence of the data.
**Weaknesses**:
- Performs poorly for high-dimensional data (i.e., many features)
- Requires a meaningful distance function to calculate similarity.
- Memory-intensive

#### Preparing Data for best results
Rescale Data:
- kNN performs much better if all of the data has the same scale.
- Normalizing your data to the range [0, 1] is a good idea.
- It may also be a good idea to standardize your data if it has a Gaussian distribution.
Address Missing Data:
- Missing data will mean that the distance between samples cannot be calculated.
- These samples could be excluded or the missing values could be imputed.
Lower Dimensionality:
- kNN is suited for lower dimensional data.
- You can try it on high dimensional data (hundreds or thousands of input variables) but be aware that it may not perform as well as other techniques.
- kNN can benefit from feature selection that reduces the dimensionality of the input feature space (more about this later in the semester).

# References
- [[mean, median, and mode]]
- [[Distance Measures]]
