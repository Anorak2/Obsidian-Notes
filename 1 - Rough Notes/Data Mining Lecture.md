## Lecture 7

$$\hat y = b + w_1x_1+w_2x_2+...+w_dx_d$$ This means that the predicted value of y ($\hat y$) is equal to the bias (b), and the sum of the features with each feature multiplied by its weight.

Alternative form:
$$f(x) = \hat y = b + \sum_{i=0}^d w_ix_i$$

How can we measure the quality of an algorithm? We take a value and then have the model predict the value associated, and then we compare that prediction with the true value.

**Measuring Error with Loss Function**

$$L(f) = \sum_{i=1}^n (y^{(i}-f(x^{(i)}))^2$$
The input is the function and the output is the loss, or how far the prediction is from the true value. When this function is averaged by n you have the mean squared error (MSE) loss.


## Lecture 8
Linear Classifiers
Model definition z(x) > 0 output class one
else output class 0


Loss Function: how good is a classifier

$$L(f) = \sum_i \delta (f(x^{(i)}))$$Finding the best classifier parameters requires an optimization algorithm

**Linear Regression Definition**
Linear combine all features using a linear regression
$$z = b + w_1x_1+w_2x_2+...+w_dx_d$$
Pass the real value z to decision function for confidence of classification.

**Sigmoid function**
$$\hat y = \sigma (z) = \frac{1}{1+e^{-z}}$$
This function is useful because it quickly ramps up both positive and negative, this helps to gain better models since it punishes all mistakes but not too much.


**Probability**
Many problems require a probability estimate as output $\hat y$, for example with a credit card application the probability of accepting an application p is a function of (accept|age, income).