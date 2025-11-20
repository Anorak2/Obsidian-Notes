
2025-11-19

Tags: [[EECS 645 - Computer Systems Architecture]]
# Cache Policies
This document is mainly focused on the disconnect between main memory and the ram/cache. Mainly that we can't directly operate on the main memory due to performance but we also have to make sure that the mismatched state doesn't lead to serious issues.
# Write Hits
## Write Through (for write hit)
---
This strategy means writing to main memory after writing to the cache, however this means we have to stall the pipeline every time we have a write hit absolutely demolishing performance (could be  5% as efficient as the original) 
## Write Behind
---
This strategy seeks to improve the write through technique by introducing a write buffer, meaning the CPU only stalls if the buffer is full. This technique works well if the rate of generating new writes is less than the time to complete writes from the buffer to main, but there can still be significant problems when we have heavy amounts of writes.

## Write Back
--- 
In this strategy we **only** update the location in the cache, and we just accept that there will be at least a temporary disconnect. This massively increases performance since due to temporal locality the same data is often modified repeatedly and now we don't need to write to memory every time.

**When is DRAM updated?** This introduces a slight problem, because if the cache is full then we need to eject a block but how do we know if it contains state? We can fix this by introducing a dirty bit that is set if the block was written to. This way we only write a block to memory when it is no longer needed in the cache. We can also combine this technique with the write buffer from before to further increase performance 

# Write Misses
What do we do if we need to write to a block but that block isn't present in the cache?
## Write Through
---
This technique is where on a write miss we fetch the missed block
1. bring current block X to cache from main memory
2. Write the new value of X from the CPU to cache
3. Write the new value of X from cache to main memory

This policy can be slow, since we have 2 calls to main memory for every single write operation, though if we repeatedly write to the same data then it might pay off. 

**Problem**
Unfortunately allocating on every write has downsides, we may try to modify an array that is larger than the cache but not currently loaded and we may not even need said array for some time after. This means that our array will clear out our entire cache and cause a large number of cache misses when the program continues executing.
## Write Around
---
To fix the previous problem what if instead we don't allocate that array to our cache at all? This technique is very efficient when we are writing data that we won't need for some time, although I believe it requires extra hardware support/cost.
# References

