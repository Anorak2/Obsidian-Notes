Tags: [[Algorithms]] [[Sorting]]
# Quick Sort Variants
As discussed in [[Quick Sort]] this is the fastest algorithm, but problematically only if we make good decisions about the Pivot selection, partition algorithm, and how we deal with the worst case

**Tony Hoare's In place Partitioning Scheme**
- Left pointer loves small items
- Right pointer loves big items
- The main idea is that we walk these towards eachother until they find something they don't like.
	when both pointers stopped, then swap and move the pointers by 1
- When these pointers cross we are done

This isn't the fastest anymore but I am very partial to it since I found it natural to implement something similar although a little slower.

![[Pasted image 20241210221518.png]]


**Using the median**
It turns out that if we use the exact median, which we can do in O(N) time, we run into the problem of it being much too slow

# References
[[Quick Sort]]