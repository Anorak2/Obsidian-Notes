
2026-01-23

Tags: [[Data Mining and Machine Learning]]
# Logistic Regression

## Linear Regression
Linear regression is interesting because of how relatively simple it actually is, the function takes a set of inputs $(x_1, x_2, ... x_n)$ and produces a single output $y$, both of which are numbers. Each input is assigned a coefficient, and a constant is also added.
$$y=B_0+B_1x_1+B_2x_2+...B_nx_n$$

**ML model with regression**
To train a model with linear regression we estimate the coefficients and then employ one of a number of techniques to improve the outcome, much like means end analysis. Some options include ordinary least squares, gradient descent, lasso regression, ridge regression.

## Polynomial Regression
![[Pasted image 20260123184503.png]]
Linear regression assumes that there is a linear relationship between the two axis, but this often isn't the case. While sometimes we can perform a transformation to make it linear, like by using a log scale, polynomial regression is another option. The simplest polynomial regression with one feature is:
$$y=B_0+B_1x_1+B_2(x_1)^2$$
With two features
$$y=B_0+B_1x_1+B_2(x_1)^2+B_3x_2+B_4(x_2)^2+B_5x_1x_2$$

## Example
```Python
x = [[0, 1], [5, 1], [15, 2], [25, 5], [35, 11], [45, 15], [55, 34], [60, 35]]
y = [4, 5, 20, 14, 32, 22, 38, 43]
x, y = np.array(x), np.array(y)

# Create an instance of the model
model = LinearRegression()

# Use the model
model.fit(x, y)

# Find the coefficient of determination (R^2)
r_sq = model.score(x, y)
```

# References
- [[Loss Functions|gradient descent]]

