
2025-03-24

Tags: [[Operating Systems]] [[Algorithms]] [[Operating Systems]]
# Practical CPU Scheduling Algorithms
The CPU scheduler is an OS component that determines which thread to run, at what time, and how long among threads in the ready queue.

**Metrics to Measure**
CPU utilization:
- % of time the CPU is busy doing something  
Throughput:
- Number of jobs done / unit time  
Response time (Turn-around time)  
- Time to complete a task (ready -> complete)  
Waiting time:
- Time spent on waiting in the ready queue  
Scheduling latency:
- Time to schedule a task (ready -> first scheduled

## First Come First Serve (FCFS)
We just assign jobs to the CPU using a queue with first come first serve. The downside is that this approach has a bad average waiting/response time

## Shortest Jobs First (SJF)
We can always do the best FIFO if we know the task's CPU burst times. We can do this by ordering jobs based on their burst lengths and then executing the job with the shortest CPU burst first.

This does come with the hard part since we can only estimate the length (this is provable), so we use the exponential weighted moving average of past bursts to do so.

This algorithm has a good average waiting/response time and is ideal if we can predict the future accurately.
## Shortest Remaining Time First
This deals with the problem of the jobs not arriving at the same time and it is a preemptive version of SJF where shorter jobs preempt longer jobs.

## Round Robin
This is FIFO but with preemption, and it is simple, fair, and easy to implement.
**Algorithm:**
- Each job executes for a fixed time slice (quantum)
- when the quantum expires the scheduler preempts the task
- schedule the next job and continue

How do we choose quantum size? if it is too short we have high overhead and too high we get bad scheduling latency
## Comparison
![[Pasted image 20250324134805.png]]

# References
[[Basic Multiprocessor Scheduling Algorithms]]
