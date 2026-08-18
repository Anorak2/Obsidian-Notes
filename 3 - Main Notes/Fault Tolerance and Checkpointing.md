
2025-05-30

Tags: [[High Performance Computing]] [[Algorithms]]
# Fault Tolerance and Checkpointing
Fault tolerance becomes a problem when we are running very long processes, such as calculating Mersenne primes, that can take hours, days, or months to run. Unfortunately our software is almost never optimal and errors can happen. **Fail Stops** are when we have crashes or hardware faults. **Silent Errors** are when we have silent data corruptions, and these can happen for any number of reasons including even cosmic radiation. Silent errors are particularly troubling because they need to be caught. The main approaches are checkpointing to recover from errors, and replication to just run it multiple times.

## Failure Distribution Rates
**Constant Failure rates ($\lambda = 1/\mu$)**
This is the "bathtub" distribution 

**Exponentially Distributed**
This is an asymptotic distribution where the inter-arrival time is  $X \space \approx \space Exp(\lambda)$, CDF is $P(X \leq t)=F(t) =1-e^{-\lambda t}$. It is also important to remember that this system has no memory, the time since the last failure tells us nothing about the time to the next failure.  
## Checkpointing / restarting
This is when we save the state, and recover from the last checkpoint if there is an error. There are two ways to implement checkpointing, at the application level or the system level. For the **application level** there is less we have to check, but it becomes complicated to implement. For the **system level** it is much easier to implement, but there is a lack of portability and a large size.


How often should we checkpoint? 
![[Pasted image 20250530184256.png]]

# References
[[Exponential CRV]]
