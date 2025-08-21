
2025-01-24

Tags: [[High Performance Computing]] [[3 - Tags/Optimization|Optimization]] [[Computer Science]]
# Gustafson's Law
Gustafson's law, rather than Amdahl's, is about weak scaling. This is where adding more processors doesn't make the runtime faster for a fixed problem, but we can get around that by increasing the scale of the problem as we increase the amount of processors used.

$$S_p=\frac{T_1}{T_p}=f+(1-f)p$$

The great thing about this is that relative to strong scaling weak scaling is much easier to achieve.

# References
[[Amdahl's Law]]