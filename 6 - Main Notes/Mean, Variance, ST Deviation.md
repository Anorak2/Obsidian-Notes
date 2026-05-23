
2026-05-19

Tags: [[Statistics Bibliography]]
## Mean and Moments
The mean is the weighted average of a set. Formally it is:
$$E[x]=\sum_x xP(x)$$
However there is a more generic version of the mean called moments, with the most important ones called the *moments* and *central moments*. The nth moment is the expected value of the service raised to the nth power.
$$E[x] = \sum_x x^n P(x)$$ Under this variation the mean is simply the first moment. The second moment is also of particular interest compared to the others.

## Variance, `stdev`, and central moments
The nth central moment is the expected value of the nth power of the difference between the service time and the mean. The formula is below: 
$$E[(x-E[x])^n] = \sum_x(x-E[x])^nP(x)$$
The second central moment is called the **variance** and the square root of variance is called the **standard deviation** (usually depicted as $\sigma$). 

Generally for variance it's easier to use the defintion
$$\sigma^2_x = E[x^2]-(E[x])^2$$


# References
- 