
2025-03-24

Tags: [[Operating Systems]] [[Operating Systems]] [[Algorithms]]
# Basic Synchronization Control
The most basic form of synchronization control is just having a producer and a consumer with a buffer in between. The problem is that sometimes we encounter a race condition. Race conditions are strictly bad since they lead to unintended behavior. 

Some solutions include mutual exclusion (only one is allowed in at a time), progress (if no one executes a critical section then someone can enter its critical section), and bounded waiting such as waiting a certain amount of time.

## Peterson's Solution
This is a software solution that doesn't require hardware support for two processes. The two processes share two variables, a flag showing whose turn it is to enter and a boolean flag to indicate if a process is ready to enter the critical section.

Thread 1:
```
do{
	flag[0] = true
	turn = 1
	while(flag[1] && turn == 1){}
	
	// critical section
	
	flag[0] = false
	
	// remainder section
} while (true)
```
This solution meets all three requirements since $P0$ and $P1$ can't be in the critical section at the same time, and if $P0$ doesn't want to enter the critical region then $p1$ does no waiting.  The limitations are that this solution only supports two processes, at least efficiently, and it assumes the LOAD and STORE instructions are atomic. It also assumes that the memory accesses are not reordered which happens often with compilers.


# References
[[Race Conditions]]

[[Locks and Semaphores]]

[[Processes]]

[[Threads]]
