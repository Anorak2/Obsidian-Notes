
[[Stats Bibliography]]

The **general approach** for turning two [[Continuous Random Variables|CRVs]] into one is to find the CDF and then take the derivative
if K = m(G,H)

$$F_K = P[K \leq k]=\int \int F_{GH}(g,h)\space dg \space dh$$
this is pretty similar to [[Transforming Discrete Random Variables|DRVs]] 


**Common Special Case** Sum of two CRVs that are dependent
Let K = G + H, to get the CDF of K we need to integrate the joint PDF $F_{G,H}$ over all (g,h) pairs such that $g+h \leq k$. But since H = K - G, this is the same as integrating over all g and over all h such that $h \leq k -g$:

$$F_K(k)=\int^\infty_{-\infty}(\int^{k-g}_{-\infty}f_{G,H}(g,h)\space dh)\space \space dg$$
This then turns into

$$f_K(k) = \int^\infty_{-\infty}F_{G,H}(g,k-g)\space dg$$
we could have also went to (k-h,h) instead

**Common Special Case, Sum of independent RVs**
In this case, the joint PDF is the product of the [[Marginal RVs|marginals]] so we get:

$$f_K(k) = \int^\infty_{-\infty}f_G(g)f_H(k-g)\space dg$$
This is called the [[Convolution Integral]] and it is absolutely fucking miserable