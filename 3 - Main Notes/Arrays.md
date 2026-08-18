
2026-03-20

Tags: [[Data Structures]]
# Arrays
An array is just a simple, uniform block of memory with a set size for each position in the array. This leads to fast retrieval times since if you want to find the memory location of an index you perform `base_address + index * sizeof(datatype)`.  In C this can be done by `*(&array[0]+index)` or equivalently `*(a + b)`, which is what `a[b]` compiles to, since the plus operator is overloaded for pointers.

| 3   | 1   | 2   | 5   | 62  |
| --- | --- | --- | --- | --- |
 ^
head

**Zero Based Indexing**
Since an array is fundamentally just a contiguous block of memory, all we need to do access the array is store the pointer to the first element. This trips up a lot of beginners but since this pointer is already at the first element to access it we do array[0]. Think of it as this location, plus however many steps you need to move over to get there.

**Efficiency**
Since arrays are a contiguous block of memory, when iterating through an array there is a minimum of $ceil((n*sizeof(\text{n's type}) / \text{cache line size})$. This may sound bad, but practically compared to many other types of data structures such as node based ones Array's are substantially faster to sequentially iterate over.
# References
- [[Cache Basics]]