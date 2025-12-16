2025-01-11

Tags: [[Algorithms]] [[Sorting]]
# Radix Sort
Radix sort is a way of (kind of) having a constant time sorting algorithm, it's fundamentally based on the idea of having an [[Formal Languages|alphabet]] with strings consisting of symbols from the alphabet. Radix sort works by leveraging the position of elements in memory, and using a stable sorting algorithm so that we don't write over our results.

**LSD**
When using LSD Radix sort we start by sorting each digit by it's rightmost character first.

The runtime is $\Theta(WN + WR)$ where W is the width of each item, N is the number of items, and R is the size of the alphabet

**MSD**
When using MSD Radix sort we start by comparing from the most significant digit first. Otherwise its the exact same idea as LSD. In practice though since the MSD is the most important, we can't take the exact same approach by doing the top digit, then the next, etc. We have to break it into sub problems, say on the first iteration we have to break it up into sub groups.
![[Pasted image 20250111203410.png]]

The runtime in the best case is $\Theta(N+R)$ since we only look at the top digit, the worst case is we have to look at every character and degenerate to LSD sort, $\Theta(WN+WR)$ 

# References
[[Counting Sort]]

[[Quick Sort]]