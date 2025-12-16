
2025-04-09

Tags: [[Operating Systems]] [[Operating Systems]] [[Data]] [[Computer Architecture]]
# Virtual Memory
We often have this abstraction where each process gets a certain amount of memory, but in practice we have to be much more conservative with our memory and the memory has to be shared with many other processes. There are a few ways to do this such as with a MMU (memory management unit) or a TLB (translation look-aside buffer) for hardware support, and for OS supported options Manage MMU and determine address mapping. Although alternatively we don't need to do virtual memory, and many real time operating systems (RTOS) don't have virtual memory.

**Problems without virtual memory**
- Not enough ram to satisfy every program
- there are gaps in our address space, we can't currently assign a continuous address space to our programs 
- Programs/process might write over eachother, so we want isolation

**Memory Management goals:**
- Easy to use abstraction
- Isolation among processes
- Don't waste memory

#### External MMU
A memory management unit is a hardware unit that transfers virtual addresses to physical addresses, and it operates as a middleman between the hardware and processes. We could define a very simple MMU as just:
	```BaseAddr```: Base Register
	```Paddr```: ```Vaddr``` + ```BaseAddr```
This approach is fast but also wasteful and offers no protection.

A better segmentation based version would look like:
	if ```Vaddr``` > limit, then trap to report an error
	else ```Paddr``` = Virtual address + Base Address
The advantages is that now we support protection between processes and variable size partitions, but it comes with the downside of now having fragmentation.

**External Fragmentation** is when the total memory space to fill a request exists but it isn't in a contiguous section.

**Paging based Modern MMU**
Modern MMU's use a paging based approach that uses the following steps:
- Divide the physical memory into fixed sized blocks called frames
- Divide logical memory into blocks of the same size called pages (frame size = page size ) 
Then we can map pages onto frames using a frame -> page table. The main advantage of this is that we no longer have external fragmentation, and now we can have efficient use of memory. However internal fragmentation (fragmentation within a page) is still possible.

The issues with paging are: that translation speed can be a problem, which isn't as big of a deal due to TLB, and the table size being large.

#### Translation Look aside Buffer
To help mitigate MMU speed issues we can use a TLB, which will cache frequent address translations so that the CPU doesn't need to access the page table all the time which makes it much faster. This buffer becomes extremely important in optimizing for cpu speed.


## Optimizing Pages
---
**Page Sizing**
We need to be careful with page sizing, if we make it very small then we minimize the amount of wasted space but we now need a very large table. If we make pages big then we have a lot of wasted space, although now the page table is small. A decent balance between the two that is commonly used in practice is 4 Kilobytes, which for a 4 GB and 32 Bit system means 1 million pages.

**Multi Level Paging**
This is when we don't have the page table directly map to the physical memory, and we instead pass through the outer page table which directs us to another page table. This process is actually very similar to [[Tree|trees]], and given enough iterations we end up with a binary tree. This allows us to save space on the map sizes since we store less redundant information.
![[Pasted image 20250409141328.png]]

**Demand Paging**
Idea: instead of keeping the entire memory pages in memory all the time, keep only part of them on a on-demand basis.

**Page table entries** are architecture specific but it can look like: valid bit for if the page is in memory, modify bit for if the page is modified, reference bit if the page is accessed, and protection bits for read/write/executable

**Page Fault** When a virtual address can not be translated to a physical address, MMU generates a trap to the OS: Step 1: allocate a free page frame, Step 2: bring the stored page on disk (if necessary), Step 3: update the PTE (mapping and valid bit), Step 4: restart the instruction
# References

