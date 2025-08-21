
[[Stats Bibliography]]
The idea of how many number of events until we observe k 1's, except here we split that into $Y$ and $Z$.
$Y =$ there are k-1 bits in the first e-1 bits
Z = 1 in the $e^{th}$ bit. We stop counting when we see the last 1

**PMF***
$$P_E(e)={{e-1} \choose {k-1}}p^k(1-p)^{e-k}$$ for $e=k, k+1,k+2, ...$, and otherwise 0

**EXPECTED VALUE**
$E[Y] = \mu_y = k/p$ 