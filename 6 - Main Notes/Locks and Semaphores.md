
2025-03-24

Tags: [[Operating Systems]] [[Operating Systems]]
# High Level Synchronization 
## Locks
Locks are a general solution to the synchronization problem that allows us to protect a critical section, we just need to acquire a lock on enter and release it on exit. On a uni-core system this means that while there is no true concurrency the threads can't be interrupted so we need to disable and enable interrupts when we are done. 

On a multicore processor we need hardware support since just disabling interrupts doesn't work anymore, so we need atomic synchronization instructions: test&set and compare&swap.

**Spinlock using Test&Set**
```
boolean TestAndSet (boolean *target){
	boolean rv = *target;
	*target = TRUE;
	return rv:
}

	int mutex
	int_lock(&mutex)
	do{
		lock(&mutex);
			//critical section
		unlock(&mutex);
	} while (true);

```
The problem with spinlocks is that they are very wasteful since we are busy waiting and the thread continues to use CPU cycles to do nothing. These are only useful when we need to hold the lock briefly. 

**Blocking lock**
Instead of spinning we just let the thread sleep so that in the meantime we can let other threads use the CPU. When the lock is released we wake up one thread. This is good for when we have a long critical section but bad for a short one since that would mean context switching.

## Semaphores
A semaphore is another high level way to solve the synchronization problem that is based around an integer variable, and wait() (or down) and signal() (or up). The semaphore itself stores how many processes are allowed to enter a certain area, and this gets decremented until we are at capacity.
![[Pasted image 20250324101730.png]]
The downside to semaphores is that they are still low level primitives, they are used for both mutual exclusion and scheduling, and they are very easy to mess up.

Semaphores work by fundamentally having two operations, a P and a V operation. P is a wait operation (or down) which decreases the semaphore value, and if the value is negative it blocks and adds itself to a queue. The V, or signal/up operation, increases the semaphores value and if there are any processes that are waiting one of them will be unblocked.

Semaphores can either be binary (0/1) which works as a lock, often for managing access to critical sections. There are also counting semaphores which restrict access to any N amount, one example might be managing access to a pool of 5 printers.

**Bounded Buffer Problem**
This is where we have a buffer that is shared between a producer and a consumer, and if it isn't full then the producer puts data in and if its not empty the consumer takes information. The problem is that the producer and consumer run asynchronously.

![[Pasted image 20250324102050.png]]

**Reader Writer Problem**
This is a many to many relationship where we have a shared object and some of the threads only read the object while several other threads write the object. Multiple readers can access the object at a time but only one writer can access the object at a time. We can solve this using two binary semaphores, a mutex for the read_count variable and a semaphore to ensure mutual exclusion for the writers with both initialized to 1.

## Monitors
A monitor is based around having a lock for mutual exclusion and condition variables for scheduling. The lock is used to protect shared data inside the monitor and the condition variables allow for threads to wait on certain events inside the monitor.

Monitors, unlike semaphores, only allow one thread in at a time.
# References
[[Basic Synchronization Control]]

[[Locking]]

[[Concurrency Control]]

[[Threads]]

[[Processes]]