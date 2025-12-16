Tags: [[Algorithms]] [[Sorting]]
# Quick Sort

Quick sort is, as the name implies, a very fast [[Formal Sorting Definition|sorting algorithm]]. It is based around the idea that we partition elements, which means moving an element (which we will call the pivot) to a position where everything to the left is smaller than it and everything to the right is larger. What is cool is that when we partition an element, the pivot value is in the correct position when the array is fully sorted.

What is interesting is that quick sort is actually the same as sorting using a [[Binary Search Trees|BST]] 


**Algorithm**
- Partition the leftmost item
- Quicksort left side
- Quicksort right side

**Avoiding Worst case**
Since Quick sort is BST sort, we can run into problems if we blindly pick a pivot since our absolute worse case would be $\Theta(N^2)$ where every value we pick is at the start or the end. The performance depends on how you pick your pivots, how you partition around that pivot, and some other optimizations.

Problems:
- Bad Ordering (an almost sorted [[Arrays|array]])
- Bad Elements (many duplicates)

Some solutions
- Randomness, pick a random pivot or shuffle before sorting
	we have to be careful with randomness since if we use the second strategy there are some places we have to be careful with for partitioning with duplicates
- Smarter Pivot Selection, calculate or approximate the median
	Quick sort requires randomness so for any pivot selection that is in constant time and deterministic there are some dangerous inputs (https://www.cs.dartmouth.edu/~doug/mdmspe.pdf). We can calculate a pivot in linear time which is safe, but slower than merge sort
- Introspection, switch to a less risky sort if too make recursive layers
	if our depth is over some limit set before then switch to merge sort, this idea is fine but for some reason not often used in practice
- Preprocess the array, though there is no obvious way to check if quick sort will be slow 

# References
[[Binary Search Trees]]
