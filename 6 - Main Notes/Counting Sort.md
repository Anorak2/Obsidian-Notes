Status:

Tags: [[Algorithms]] [[Sorting]]
# Counting Sort

Counting sort is a type of [[Formal Sorting Definition|sorting algorithm]] that works by exploiting space, we can do this by creating a bunch of buckets for elements and putting items into their appropriate bucket. We can use counting sort to sort N elements in $O(N)$ time.

The problem with using counting sort on its own is that it requires a huge amount of [[Arrays|arrays]] for larger items, similar to a naive [[Hash Tables|hash table]] implementation.

**Performance**
If we need to create R arrays for quick sort to work, we can expect reasonable efficiency if $N \geq R$ 

# References
[[Formal Sorting Definition]]

[[Arrays]]

[[Hash Tables]]