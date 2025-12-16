
2025-11-12

Tags: [[Computer Architecture]]
# Cache Associativity
**Fully Associative** caches are when we allow a given block to go in any place in the cache, but this requires that all entries are searched O(N) and it is expensive since it requires a comparator per entry.

**N-way Set Associative** caches are when each set contains n entries and the block number determines which sets, simply `block num % sets in cache`. This way we search all entries in a given set at once and only using n comparators (less expensive).

The spectrum of associativity can be seen below:
	Direct Mapped = 1
	N-Way associative = n
![[Pasted image 20251112154046.png]]

## Replacement Policies
--- 
Direct mapped: 
- no choice

Set associative
- Prefer non-valid entry, if there is one
- Otherwise, choose among entries in the set

Replacement Policies
- Least-recently used (LRU)
	Choose the one unused for the longest time
	Simple for 2-way, manageable for 4-way, too hard beyond that
- FIFO (first-in-first-out)
- NMRU (not most recently used)
- Random/Pseudo-random
	Gives approximately the same performance as LRU for high associativity


# References
[[Cache Basics]]

[[Direct Mapped Caches]]

