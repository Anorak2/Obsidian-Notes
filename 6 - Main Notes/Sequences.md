
2025-09-02

Tags: [[Calculus Bibliography]] [[Math]]
# Sequences
A sequence is a list of numbers written in a specific order, and a sequence doesn't have to start at a specific value such as 1 or 0. Sequences are also functions that only take in ascending integers as their inputs.

## Limits of Sequences
We say that a sequence converges to a limit L and write the formula below if we can make the terms $a_n$ as close to L as we like by taking n as sufficiently large.
$$\lim _{n \to \infty} a_n = L \space \text{ or } a_n \to L \text{ as } n \to \infty $$

If no limit exists then we say that $a_n$ diverges, and if the terms increase without bound we say that $a_n$ diverges to infinity

## Theorems
#### Theorem 1
if $\lim_{x \to \infty} f(x)$ exists then the sequence $a_n = f(n)$ converges to the same limit
$$lim_{n \to \infty} a_n = \lim_{x \to \infty} f(x)$$
![[Pasted image 20231004212403.png]]
#### Theorem 3
Let $a_n, b_n, c_n$ be sequences such that for some number M 
$$b_n \leq a_n \leq c_n \text{ for } n > M \ \ \ \ \text{ and }  \ \ \ \  \lim_{n \to \infty } b_n = \lim_{n \to \infty} c_n = L$$
#### Theorem 4
If f is continuous and $\lim_{n \to \infty} a_n = L$ then:
$$\lim_{n \to \infty} f(a_n) = f(\lim_{n \to \infty} a_n) = f(L)$$
# References
[[Limits]]
