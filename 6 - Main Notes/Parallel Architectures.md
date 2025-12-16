
2025-01-24

Tags: [[High Performance Computing]] [[Computer Science]]
# Parallel Architectures
There are four main types of parallel architectures; SISD, SIMD, MISD, and MIMD. These can really be simplified though to systems with a sequential instruction set (SI) or multiple (MI) and systems with either a single source of data or multiple data sources. SISD is the most basic, and its just like a serial one core computer. SIMD would be like a graphics card since it is able to be parallelized but it has one instruction set, SIMD is fantastic for performing one operation on a matrix. There are no MISD systems, and MIMD is the realm of super computing, servers, and clusters.

### Memory Structures

![[Pasted image 20250124132541.png]]
**UMA**
By memory structures you can have a few different approaches, the simplest being shared memory (UMA) where CPU's all have the same level of access to the same pool of memory. All of the processors have equal latency to all memory locations. The downsides are in [[Parallel Computation Models]] since the memory is shared there are conflicts

**NUMA**
Non unified memory architecture would be like the picture on the right where each CPU can access each section of memory. Some CPU's are closer than others which means that there is an unequal access latency since the links are slower.

**Parallel Architecture model**
![[Pasted image 20250124132942.png]]
Processors get their own local memory which isn't shared, and they are linked by some kind of connection like ethernet. The advantage is that this approach is very scalable but at the cost of being harder to program and having an added communication cost

**Hybrid Distributed Shared Memory**
![[Pasted image 20250124133132.png]]
This is the technique being used my most modern supercomputers and it involves having distributed memory across multiple machines (nodes) which are then connected to other nodes over a network. This is an even more scalable approach since we get the benefits of both, but at the cost of being even harder to program
# References
[[Threads]]

[[Processes]]