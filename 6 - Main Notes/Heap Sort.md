Status: 

Tags: [[Algorithms]] [[Sorting]]
# Heap Sort

Rather than scanning the entire [[Arrays|array]] for an element like [[Selection Sort]] we can maintain a [[Heaps|heap]] to ensure that our selection is fast. The overall runtime for this algorithm is actually $O(n \log n)$, and while the Naive implementation takes O(n) memory we can fix that by doing an in place heap sort.

**In place Heapsort**
Rather than create a new heap, we can just treat the input array as a heap. We can do this by using "bottom up heapification", and once we turned the array into a heap its basically the same as the naive heap sort.

- Bottom up heapify input array
- Repeat N times
	- Delete largest item from the max heap, swapping root with last item in the heap

**Naive Heapsort Algorithm**
- Insert all elements into a Max [[Heaps|heap]] and discard the input array
- Create output array
- Repeat N times
	- Pop largest item from the max heap
	- Put largest item at the end of the output array

# References
[[Heaps]]