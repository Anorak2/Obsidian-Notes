
2025-01-24

Tags: [[High Performance Computing]] [[3 - Tags/Optimization|Optimization]] [[Computer Science]]
# Amdahl's Law
Amdahl's law deals with any code with a parallelizable section of code, and a serial section of code. The law states that adding more processors (scaling) can make the program faster but we are always capped by the runtime of the serial section
$$S_p =\frac{T_1}{T_p}=\frac{1}{f+\frac{(1-f)}{p}} \leq \frac{1}{f}$$
where f is the fraction of code that is sequential. 

This is referred to as strong scaling, since we are solving a fixed sized problem and every added processor means that we can solve the problem faster. This is really hard to achieve, and because of this cap in the 60's and 70's production of parallel architecture was slowed

# References
[[Gustafson's Law]]