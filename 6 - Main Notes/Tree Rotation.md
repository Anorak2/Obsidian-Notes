
2024-12-27

Status:

Tags: [[Data Structures]]
# Tree Rotation
Tree rotation is an operation that lets us change the structure without messing with the order of the elements contained by a tree.
![[Pasted image 20241227215939.png]]
This is very useful because this means we can balance out [[Binary Search Trees]] without messing up their sorted nature. However while this does work, in practice we don't like to spend $O(N)$ every now and then re-organizing our data. We can get around this restriction by choosing a form of tree that is bushy by nature, [[B-Trees]].
# References
[[Tree]]

[[Binary Search Trees]]

[[B-Trees]]