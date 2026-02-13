
2025-11-12

Tags:
# Cache Basics
Cache memory is the level of memory hierarchy closest to the CPU. Each line in the cache is also called a block and each block can store multiple words of 32 bits. If we find the data we are looking for in the cache we call that a **hit**, otherwise we call it a cache **miss**. On a cache hit we proceed as normal but on miss we stall the CPU pipeline and fetch the block from the next level of hierarchy.

**Cache miss steps:**
- Reset PC by PC-4
- instruct main memory to send the missed instruction
- write the instruction back to the cache
- update the tag field
- update valid bit
- restart the instruction execution

**Ideally** each word in memory directly refers to a unique address in the cache and the location is determined by memory address. The challenges with that is mismatched memory size, say the cache might be 8 MiB and the Ram might be 4 GB. Also, the operating system generates a fixed address that is often 64 or sometimes 32 bits long but a 2 MB cache would only need 15 bits leading to wasted space.

## Instruction Caches
While data and code used to be treated the exact same, engineers long ago realized that it was more efficient to have separate caches for code and for data. One example of how that might look is below.
![[Pasted image 20260119223622.png]]
The main reason why we do this is that the memory regions for the data and instruction caches are essentially independent, so by separating the two of them interference is reduced. 
## Useful Equations
![[Pasted image 20251112152841.png]]

# References

