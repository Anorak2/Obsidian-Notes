
[[Stats Bibliography]]

We already have results for a specific case since any linear combination of [[Gaussian (normal) CRV|Gaussian]] CRVs is Gaussian.

**Derived RV from one CRV**
The general approach for a CRV G, to get PDF of k = m(g):
1. Determine CDF of K: $F_K(k)=P[K \leq k]$
2. Take derivative of CDF to get PDF: $f_K(k)= \frac{d}{d\mu}F_K(k)$ 

General result for positive scaling:
For $K = m(G) = aG$ **With a > 0**, the end result is
$$f_K(k)=\frac{1}{a}f_G(\frac{k}{a})$$ Case where G is [[Exponential CRV|Exponential]]($\lambda$) and $K = aG$ **with** a > 0

$$F_K(k) = Exponential(\frac{\lambda}{a})$$ Case for shifting:
$K = G+b$ where here b can be negative
$$F_K(k)=F_G(\mu-b) \space so \space F_K(k) = F_G(k-b)$$

For K=m(G) with m() strictly monotonic and $G = n(k)=m^{-1}(k)$
$$F_K(k)=f_G(n(k)) \cdot|n'(k)|$$
