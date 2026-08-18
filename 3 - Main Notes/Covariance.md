

2026-02-01

Tags:  [[Statistics Bibliography]] [[Data Mining and Machine Learning]]
# Covariance

**Formal Definition**
$$Cov[G,H] = \sigma_{GH}= E[(G-\mu_g)(H-\mu_H)] $$
OR
$$Cov[G,H] = \sigma_{GH} = E[GH] - \mu_G \space \mu_H$$

While [[Variance and ST Deviation|variance]] is always positive, covariance can be positive, negative, or 0.

**WHAT COVARIANCE TELLS US**
Informally covariance is said to measure how far a set of (random) numbers are spread our from their average value, and in machine learning it measures the interdependence between two features.

If ($G \space \mu_G$) and ($H \space \mu_H$) have the same sign, then the product will be positive. Otherwise the product will be negative. This means that the sign of $\sigma_{GH}$ gives us info about the tendency of G and H to be on the same side of their means ($\sigma_{GH} > 0$) or on opposite sides. In general, a large/smaller magnitude of $\sigma_{GH}$ indicates that G or H tend to be further/closer to their means.

We have to be careful though because covariance can vary significantly based on which units are used.

## In machine learning
$$cov(X,Y) = \frac{1}{n}\sum_{i=1}^n(x_i-E(X))(y_i-E(Y))$$
where:
$E(X) = \mu_x = \text{ mean of x for all samples}$ 
$E(Y) = \mu_y = \text{ mean of y for all samples}$ 

Often covariance is represented as a matrix, seen below, with the diagonal representing variance of a feature. If the non-diagonal features have a covariance of 0 then they are independent. Something to be wary of is that covariance in it's usual form isn't normalized and thus can vary significantly based on the scale (units) used. 
![[Pasted image 20260201165725.png]]

**Sign:**
The greater the value of one feature, the greater the correlation between the two features. Given a negative value the opposite is true, the behavior of one feature causes the opposite reaction in another. 

### Correlation Coefficient
This is simply covariance but normalized to a value between 0 and 1 showing the degree to which two features depend on eachother. They are normalized so that, in the matrix above, each row and column adds up to one.

# References
[[Variance and ST Deviation]]