
2025-04-09

Tags: [[Operating Systems]] [[Operating Systems]] [[Data]]

# Virtual Memory 2
**Memory Mapped I/O**
Idea: map a file on disk onto the memory space. Benefits: you don’t need to use read()/write() system calls, just directly access data in the file via memory instructions

**Illusion of Infinite Memory**
Demanding paging allows more memory to be allocated than the size  
of physical memory, it uses memory as cache of disk.

What to do when memory is full? On a page fault, there’s no free page frame so someone (page) must go (be evicted).

**Page Relocation**
On a page fault  Step 1: allocate a free page frame: if there’s a free frame use it, if there’s no free frame, choose a victim frame and evict it to disk (if necessary) → swap-out. Step 2: bring the stored page on disk (if necessary). Step 3: update the PTE (mapping and valid bit). Step 4: restart the instruction.

**Page Replacement Policies**
FIFO (First In, First Out)
- Evict the oldest page first.
- Pros: fair
- Cons: can throw out frequently used pages

Optimal
- Evict the page that will not be used for the longest period
- Pros: optimal
- Cons: you need to know the future

Random  
- Randomly choose a page  
- Pros: simple. TLB commonly uses this method  
- Cons: unpredictable  

LRU (Least Recently Used)  
- Look at the past history, choose the one that has not been used for the longest period  
- Pros: good performance  
- Cons: complex, requires h/w support

**Thrashing**
A processes is busy swapping pages in and out doesn't make much progress, this happens when a process do not have “enough” pages in memory. Very high page fault rate, low CPU utilization, CPU utilization based admission control may bring more programs to increase the utilization → more page faults.

**Copy On Write (COW)**
imagine a process where fork() creates a copy of a parent process, should we copy the entire pages onto the new page frames? if the parent uses 1 GB of memory then a fork call would take a long time, especially wasteful if we then immediately did something like an exec call. Instead we can just copy the page table of the parent so that both the parent and the child point to the same physical page frames.

reuse those same pages right up until we need to write to one, and then we copy the page so that we can write to it


# References
[[Virtual Memory]]

[[Processes]]