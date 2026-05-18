
2026-04-14

Tags: [[High Performance Computing]] [[Software Engineering]]
# Monitors
Monitors are a high-level synchronization mechanism that simplify process and thread synchronization. They are built on top of locks and are mostly used in multithreading systems. Unlike semaphores, where the programmer must explicitly call wait() and signal(), monitors combine both the shared data and operations on that data inside of a single structure, making synchronization safer and easier to manage. 

key features are:
- only one thread at a time has mutually exclusive access to a critical code section
- threads running in a monitor could be blocked while they’re waiting for certain conditions to be met
- one thread can notify other threads when conditions they’re waiting on are met


## Implementations
Monitors are implemented at the programming language level, not directly by the operating system. In Java, monitor-like behavior is achieved using the synchronized keyword ensures that only one thread can execute inside the monitor at a time.

Fundamentally however, we accomplish mutual exclusion using Mutex Locks associated with every object and class. The difference is that from a programmers perspective a lot of the manual locking.setting is abstracted out. This is why we say Monitors are implemented only at the codebase level since they compile down to these Mutex Locks.
# References
- [[Mutex Locks and Semaphores]]