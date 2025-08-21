
2025-02-06

Tags: [[High Performance Computing]] [[Computer Science]] [[Algorithms]]
# Basic Multiprocessor Scheduling Algorithms

Makespan lower bound = Max{the longest process, if we have perfect loading}

## P | $pmtn$ | $C_{max}$ 
Schedule n jobs on m identical processors to minimize makespan

Here the optimal algorithm is called McNaughton's wraparound
- Schedule n jobs in any order
- Fill up the m processors one job at a time
- if a processor can't finish a job then we can split it in two and keep going

run time is $O(n)$ since we just need to run through the algorithm one time

**Optimality**
- This algorithm is optimal since by splitting the jobs the makespan equals the lower bound

**Feasibility**
- Jobs can't overlap, since if they did then that means the lower bound is incorrect. This is a contradiction since we can't have a job longer than the lower bound
- There is enough space because $LB \geq \frac{E_j \space P_j}{m}$
## P | | $C_{max}$ 
This problem is Strongly NP-Hard

**Solutions**
- Exact algorithms (best solution, exp time)
- Heuristics (best effort, no guaranteed runtime)
- Approximation (polynomial time + performance guaranteed)

## P | | $C_{max}$ - LIST Scheduling
This is a greedy algorithm
1. Arrange n jobs in any order
2. Assign a job to the processor with the least total load so far

This approach is $O(n \lg m)$ for its runtime, and we can prove that it will get within a 2-approximation of $C_{max}$ 
## P | | $C_{max}$ - LPT Scheduling
- Sort the Jobs in a decreasing order
- Iterate through the jobs, which are in the greatest first order, and assign the job to the least loaded processor

This approach allows the smaller jobs to "fill in" the cracks, and this algorithm is a **4/3 approximation** for P | | $C_{max}$ 

## Can we do better?

yes we can using approximation schemes
# References
[[Multiprocessor Scheduling Notation]]