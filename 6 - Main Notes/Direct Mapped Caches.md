
2025-11-12

Tags: [[EECS 645 - Computer Systems Architecture]]
# Direct Mapped Caches
---
In a direct mapped cache each word can only go to **one** location in the cache, or in other words the associativity is 1. We can determine this address by taking the block address from the CPU modulo the number of blocks in the cache. The block address can be found by `floor(byte address)/block size`
![[Pasted image 20251112151908.png]]
Above is an example of a direct mapped cache with only 8 entries.

## Tags and Valid Bits
---
In direct mapped cases multiple addresses can map to a single block in the cache, leading to the problem of how do we know which one is currently loaded. We can solve this by storing the **tag**, ie the high order bits in the address. We can do this because the low order bits are already known since they remain after the modulus.

When the CPU is just starting the cache is empty and all current data blocks are invalid, hence why we also add a **valid** bit set to one if it's present and 0 if it's empty.

# References
[[Cache Basics]]

[[Cache Associativity]]