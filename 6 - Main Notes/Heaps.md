Status: 

Tags: [[Data Structures]]

Heaps are a way of storing elements such that they are ordered with either the maximum or minimum element at the front, and we can remove that element and the next largest/smallest element will take its place. We could do this using some types of BST or others, but they are kind of annoying, so what we do instead is we create a complete tree. When we want to add an element to our heap we can just add it to the end of this tree, and then move it up the tree until it isn't "better" than its parent which becomes its rightful place.

| Min Heap       | Ordered Array | Bushy BST   | Hash Table | Heap        |
| -------------- | ------------- | ----------- | ---------- | ----------- |
| add            | O(N)          | O($\log n$) | O(1)       | O($\log n$) |
| getSmallest    | O(1)          | O($\log n$) | O(N)       | O(1)        |
| removeSmallest | O(N)          | O($\log n$) | O(N)       | O($\log n$) |

**Delete Minimum**
To delete the minimum what we do is we swap the very last element in the heap with the first element, and then we start sinking it down the heap replacing our current position with more qualified positions.

**Methods**
Heaps have getSmallest(), getLargest(), and add(x)

**Implementation**
to implement our data structure we use an [[Arrays|array]], this is because [[Arrays]] can actually correctly model a [[Binary Search Trees|BST]] so long as it is complete. We also usually by tradition leave the first element blank so as to make it look a little nicer,

- parent = index/2
- left child = index * 2
- right child = index * 2 + 1


or by default:
- parent = (index - 1)/2
- left child = Index * 2 + 1
- right child = index * 2 + 2

# References
[[Heap Sort]]
