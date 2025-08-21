
2025-02-11

Tags: [[Algorithms]] [[Computer Science]] [[High Performance Computing]]
# $P | Size_j  | C_{max}$
These are jobs where we allow parallelization without preemption, and this is a strongly NP-Hard problem since $P||C_{max}$ is a special case where each m = 1.

## Reservation Based Scheduling
We create a priority queue to hold all of our processes and then we iterate through giving each processes the earliest time.

This is a fairly simply idea but this approach kind of sucks and is only able to give us a 3 approximation of the $C_{max}$ 

## Pack Based Scheduling
- Organize by priority
- put job 1 into pack  until we can't fit anymore jobs 
- execute all of the jobs in pack
- Repeat until no more jobs

This approach is also a 3-approx unfortunately, there are some ways to optimize such as first fit which is a 2.7 (?) approx.

## Greedy Based Scheduling
- Organize jobs in any order, it can be priority based
- at $T_0$ or whenever a job completes:
	- Check each job in the list, if we can run it then run it

This approach is able to give us a 2-approx of $P|size_j|C_{max}$ 

## In Practice
In practice reservation (FIFO) + Backfilling is used
- Jobs queued first come first serve
- A job is back filled if it can be executed without affecting other jobs

**Conservative Backfilling**
- Reservation for each job
- hard to backfill

**Easy Backfilling**
- only make a reservation for one job, other jobs have a tentative placement
- Back fill job to current time
	- assign jobs priorities 
	- this approach has no job starvation

Most schedules require rigid parallel information, and an approximation of:
1. Processor requirement
2. Space
3. Time

## Others
Adaptive scheduling is where we dynamically adapt processor applications

Multi-dimensional scheduling

Issues under estimating:
- Delayed job completion
- wasted system resource
- uncertainty aware scheduling

issues over estimating:
- longer wait times
- user is punished
- may waste resources

# References
[[Multiprocessor Scheduling Notation]]

[[Basic Multiprocessor Scheduling Algorithms]]