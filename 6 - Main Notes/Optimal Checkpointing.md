
2025-05-30

Tags: [[High Performance Computing]] [[Algorithms]]
# Optimal Checkpointing

Assumptions
1. Failures are exponentially distributed at a rate of d = $1/\mu$, which is the mean time between failure
2. There are no failures during recovery and checkpointing
3. C and R costs are constants that are less than $\mu = 1/\lambda$ 

## Recursive Solution:
$$
E(T)=D_{fail}\cdot(E_{lost}+R+E(T))+((1-P_{fail})\cdot(t+C)\cdot P_{fail} \cdot E_{lost}
$$
$$P_{fail}(x \leq T) = 1-e^{-\lambda t}$$
$$E_{lost}(t) = \int_0^t t\cdot P(x=t | x \leq t)\space  dt$$
anyways after maybe some extra mess, the first order approx is T/2. and the exact solution is:
$$ 
E(T)=(e^{\lambda T -1})(\frac{1}{\lambda}+R)+C
$$
## Optimal Checkpointing for Linear Workflow
This is where we have a set of tasks with a linear dependency chain
- Each task has a failure-free execution time of $Ti$ $\forall i = 1..n$ 
- Checkpoints are only allowed at the end of a task
- assume the last task n is checkpointed

The question is what should be the optimal checkpointing strategy? Or another way, which tasks should be check pointed to minimize the total expected computation time?

The naive method is to try all $2^{n-1}$ possibilities, but we can actually use dynamic programming to solve this.
- E(i): Optimal expected execution time from task 1 to task i assuming task i is checkpointed
- E(i) = $min\{E(j) + E(j+1, i)\}$, where task j is the last checkpointed task before i. The final solution is E(n) and the total runtime is $O(n^2)$  

## Optimal Checkpointing for preemptable long run job
In this version of the problem we can put a checkpoint anywhere we'd  like, and the goal is to find an optimal period T to minimize overhead.
$$\text{overhead}=H(T)=\frac{E(T)}{T}-1=\frac{(E^{\lambda t}-1)(\frac{1}{\lambda}+R)}{T}-1$$
1. The exact solution depends on the the Lambert W function, idk what that is
2. The first order approximation solution however is:
$$T* = \sqrt{\frac{2c}{\lambda}}=\sqrt{2\mu c}$$
$$ \mu = \frac{1}{\lambda}$$ 
```Young-Daly``` Formula
# References
[[Fault Tolerance and Checkpointing]]

[[Dynamic Programming]]

[[Taylor Series*]]