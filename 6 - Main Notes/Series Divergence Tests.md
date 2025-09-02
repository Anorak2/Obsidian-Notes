

2025-09-02

Tags: [[Calculus Bibliography]] [[Math]]
# Series Divergence Tests

## Nth Term Divergence Test
if $lim_{n\to \infty} \space a_n != 0$  then the series does not converge, we can just move on. Otherwise we have to go to another test

## Limit Comparison Test
let $a_n$ and $b_n$ be positive sequences. Assume that the limit below exists

$$ L = \lim_{n \to \infty} \frac{a_n}{b_n}$$
- if $L > 0$, then $\sum a_n$ does what  $\sum b_n$ does
- if $L = \infty$ and $\sum a_n$ converges, then $b_n$ converges
- if $L = 0$ and $\sum b_n$ converges, then $\sum a_n$ converges
## Alternating Series Test
Assume that $b_n$ is a positive series that is decreasing and converges to zero, if we can meet these three conditions then the following alternating series converges

$$\sum^\infty_{n=1}\space(-1)^{n-1}b_n = b_1 - b_2 + b_3 - b_4 ...$$

this test can only show convergence though, not divergence

### Error
if $a_n$ converges by the A.S.T., then the error is $|S-S_n| < b_n +1$


## Direct Comparison Test
Assume there exists M > 0 such that $0 \lt= a_n \lt= b_n$ for all n > M

then if the function M is "bigger" than the original, and it converges, then the original also converges. If the function M is smaller than the original, and it diverges, then the original also diverges. 

if it doesn't fit either of these two then we can't say anything and we have to use a different test, often the **Limit Comparison test**.

## Integral Test
let $a_n = f(n)$ where f is a positive, decreasing, and continuous function of x for x >= 1. This test kinda sucks but if the function:
$$ \int^\infty_1 f(x) fx$$ converges or diverges, then the series:
$$\sum ^\infty_{n=1} a_n$$ also correspondingly converges or diverges.

## Ratio Test
when  testing a sequence with the ratio test we use:
$$p =\lim_{n \to \infty}\space |\frac{a_{n+1}}{a_n}| =\lim_{n \to \infty}\space a_{n+1} * a_n^{-1}$$
we then group like terms and try to cancel out as much as we can.

if p < 1, then $\sum a_n$ converges absolutely
if p > 1 then $\sum a_n$ diverges
if p = 1 then the test is inconclusive

## Root Test
if the following limit exists:
$$R = \lim_{n \to \infty} \sqrt[n]{|a_n|}$$
if R < 1, then $\sum a_n$ converges absolutely
if R > 1 then $\sum a_n$ diverges
if R = 1 then the test is inconclusive

# References
[[Series]]

[[Calculus Bibliography]]
