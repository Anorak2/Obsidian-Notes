
2026-05-19

Tags: [[Software Engineering (SWE)]] 
# Service Time distributions
## Probability Distributions
Firstly, it is impractical to try and generate an exact model. Doing so requires an unreasonably expensive amount of knowledge, so we tend to work instead with averages and simplified views. 

However computing a simple probability distribution comes with assumptions that are being made. We generally assume that distinct service times are independent and identically distributed. This isn't always true but it is reasonable to assume.

**Finite Spaces**
If the sample space is finite then we are able to use relatively simple methods such as iterating through every possible option. Form there we have tools such as mean, variance, coefficient of variation, the second moment, etc.

The mean gives us an indication of the magnitude of service time, and the variance gives us an indication of variability (consistency). Since we would also like a more direct way to show variability we also use the *coefficient of variation*.  Typically for processor service times $C_x$ values of 10 or more aren't unusual, while for I/O service times typically values of $C_x$ less than one are typical. 

**Infinite Spaces - Discrete**
It's unusual to have a finite space, and thus we can't simply brute force the values. If the values are discrete then we may be able to characterize them with a function, in these cases the Geometric Distribution very important. Usually we won't use geometric distributions to to represent service times directly, but we can characterize random variables by probability distributions.

**Infinite Spaces - Continuous**
This is the most common case for service times. It's also worth a reminder that for continuous distributions we are only interested in ranges of values.
# References
- [[Mean, Variance, ST Deviation]]
- [[Coefficient of Variation]]
- [[Geometric Distribution]]
- 