
[[Stats Bibliography]]
This should be called the [[Covariance]] coefficient but it isn't. this is what we use to normalize [[Covariance]] so that we can tell what a "lot" of covariance is.

**DEFINITION** 
$$\rho_{G,H} = \frac{Cov[g,h]}{\sqrt{var[h]var[h]}} = \frac{\sigma _{G,H}}{\sigma_G \space \sigma_H}$$
The point is that since the top and bottom have the same units, now the result is dimensionless.

**PROPERTIES**
$-1 \leq \rho_{G,H} \leq 1$

**WHAT IT TELLS US**
$\rho_{G,H} > 0$ means that G and H are positively correlated (more likely to have same signs than opposite)

$\rho_{G,H} < 0$ means that G and H are negatively correlated (more likely to have opposite signs than same)

$\rho_{G,H}$ close to 0 means that there is a weak correlation, and the closer it is to -1 or 1 the higher the correlattion 