
2025-03-24

Tags: [[Operating Systems]] [[Operating Systems]] [[Algorithms]]
# Deadlocks

Deadlocks don't just happen, in fact four conditions need to be met:
1. Mutual Exclusion, only one process at a time can use a resource
2. No preemption, release must be voluntary
3. Hold and wait, a process must be holding at least one resource and waiting to acquire resources held by other processes
4.  Circular wait, there has to be a circular dependency were A requires C and C requires A
All four conditions must hold for there to be a deadlock, and on it's own a deadlock can't resolve

**Methods to handle deadlocks**
We can handle deadlocks with detection and recovery, where we detect that a deadlock occurred and then recover to a safe state. To do this we need an algorithm that can detect deadlocks and also to preempt resources.

The other approach is to prevent and avoid deadlocks to ensure the system never enters a deadlock. The solutions could be to have "infinite resources", prevent hold and wait, and to prevent circular waits

## Deadlock detection
**Single Instance per Resource**
Each resource is unique, which means one printer one network card etc. We then just have a wait for graph and search for a cycle in the wait for graph which if present points to the existence of a deadlock

**Multiple instances per Resource**
Basically the same as the single resource version just now we can request part of a resource.

## Recovery from Deadlock
**Terminate**
We preempt the resources, and then kill the deadlocked threads and return the resources.

**Rollback**
We return to a known safe state

We have to be careful because it's not always possible to fix a deadlock

**Prevention**
We just need to break any of the four conditions. 
1. We can share more resources and not have locks but not all resources are shareable
2. We can allow preemption but this is also hard
3. Instead get all of the resources at once
4. We stop cycles from forming, if there is a step that will cause a cycle we prevent it

## Banker's Algorithm
The idea is that we assume that each processes maximum resource amount is known in advance and we pretend each request is granted and then run the deadlock detection algorithm. If we detect a deadlock then we don't grant the request to keep the system in a safe state

# References
[[Basic Multiprocessor Scheduling Algorithms]]

[[Processes]]
