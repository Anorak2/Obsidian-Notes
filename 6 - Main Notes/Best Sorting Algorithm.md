Status: 

Tags: [[Algorithms]] [[Sorting]] [[3 - Tags/Optimization|Optimization]]
# Best Sorting Algorithm

What is the best sorting algorithm? it depends

When is [[Radix Sort]] faster?
- Sufficiently large N
- Strings are very similar to eachother
	- Each comparison costs $\Theta(W)$ time

When is [[Merge Sort]] faster?
- if strings are highly dissimilar to eachother
	- each Merge Sort comparison is very fast

if we have 100 strings each with 1000 characters that are identical then Radix sort will need 100,000 comparisons. Merge sort on the other hand takes ~660,000 comparisons.

# References

[[Radix Sort]]

[[Merge Sort]]