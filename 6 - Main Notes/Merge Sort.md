Status:

Tags: [[Algorithms]] [[Sorting]]
# Merge Sort

Merge sort is a recursive [[Formal Sorting Definition|sorting]] algorithm that is based around the idea that it is easy to merge two lists that are already sorted. The algorithm has a $\Theta(n \log n )$ runtime, and a space complexity of $\Theta(n)$ when using an auxiliary array. It is possible to do an in place merge sort but the algorithm is very complicated and performance takes a noticeable hit.

**Algorithm**
- Split [[Arrays|array]] into roughly two even halves
- merge sort each side (since this is a recursive algorithm)
- Merge the two sorted halves to form the final result
	- Compare the input[i] with input[j] if necessary (where i is where the left side starts and j where the right side starts)
	- copy the smaller item to the end of the aux array and increment i or j

# References
