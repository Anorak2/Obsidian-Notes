
[[Stats Bibliography]]

When sampling we are working with many different random variables being joined together, and this is a problem since if we have $G_i$ cases that are independent it is possible to get the PDF as $f_{T_n}=f_{G_1}(g_1) \space * \space ... \space * f_{G_n}(g_n)$ where here * represents the [[Convolution Integral]]. This is a huge pain in the ass. However, since $T_n$ is a function of RVs, it is also a RV with a mean, variance, etc.

**Mean**
For any RVs $G_1,G_2,...G_n$ the mean of their sum is:
$$E[T_n]= E[G_1]+...+E[G_n]=\sum^n_{L=1} E[G_1]$$

**Variance**
$$Var[T_n]=\sum^n_{I=1} \sum^n_{J=1} \space Cov[G_i, G_j]$$
However, due to some reasons I don't care to write we only need to sum from j=i+1 to h and double it. 

General Result:
$$Var[J_H] = \sum^n_{i=1} Var[G_i] +2\sum_{i=1}^n \sum^n_{J=I+1} Cov[G_i, G_J]$$
