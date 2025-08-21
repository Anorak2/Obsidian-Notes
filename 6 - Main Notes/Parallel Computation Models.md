
2025-01-24

Tags: [[High Performance Computing]] [[Computer Science]] [[3 - Tags/Optimization|Optimization]]
# Parallel Computation Models

### PRAM
PRAM, short for parallel random access machine is a model used to analyze the time complexity of parallel algorithms. For this model we ignore all synchronization and communication. This means all cores have the same latency, as it works in UMA. the problem is there are conflicts due to this shared memory, leading to four approaches to fix this

- *EREW*: Exclusive read, exclusive write. This is the most restrictive since no two processors can use the same location at the same time
- *CREW*: Concurrent read, exclusive write
- *ERCW*: Exclusive read, concurrent write
- *CRCW*: Concurrent read, concurrent write. This is the most powerful model but also has some problems

Concurrent writes are handled with a couple approaches:
- Common: all processors must write some kind of common values
- Arbitrary: one value is arbitrarily selected
- Priority: Processors have an assigned priority which takes precedence
- Combination/reduction: sine combination between the overlapping requests is used 
The difference between these isn't very large since CRCW can be simulated to EREW with a time of only $O(\log n)$. 

### BSP
This approach, Bulk Synchronous Parallel, is different from PRAM since we now account for communication and synchronous costs as well. BSP has a set of steps that always take place:
1. Local computation, where local work is done by all processors using local data
2. Communication, processors communicate and exchange data among eachother
3. Barrier Synchronization, conclusion of a super-step and separation from the next super-step 
![[Pasted image 20250124134641.png]]

### LogP
This model is different from BSP since this model also now allows us to account for asynchronous communication, and the cost for that communication is how this model got its name. 
- L, Latency of Communication
- o, overhead of sending/receiving communication
- g, gap between successive sends and receives
- P, number of processors
Ex:
$$Cost = L + 2o +p$$ 

# References
[[Parallel Architectures]]

[[Threads]]
