Status: 

Tags: [[Data Structures]]
# B-Trees

B-Trees, or otherwise known as 2-3 or 2-3-4 trees are a way to fix the problems [[Binary Search Trees]] have when they get spindly, and B-trees are a unique way to auto balance a tree so that it is **always** bushy, and although we have nodes with multiple values in them, since the nodes always have a constant amount of numbers in them it doesn't matter for the overall time complexity. The main downsides are that B-Trees are hard to implement and they have some annoying performance problems.

| Time Complexity | Contains      | Insert        | Delete        |
| --------------- | ------------- | ------------- | ------------- |
| Worst Case      | O($n \log n$) | O($n \log n$) | O($n \log n$) |
**Idea**
The basic idea is, what if instead of having an unbalanced tree we simply overstuffed nodes (sort of like [[Arrays]]). This is a pretty weird idea, but the problem is that eventually we can just end up with a list which has an O(n) traversal time.

The way that we fix that is that when a node gets too full, we can just move it up a layer instead.

![[Pasted image 20241128012130.png]] ![[Pasted image 20241128012146.png]]

But what happens if any non-leaf node gets full? don't worry, we can just split those nodes too. In fact, the only way a B-Tree can increase its depth is by splitting the root node. A cool thing to note here though, is that the tree we've created is **Perfectly Balanced** and that isn't an accident that is always true. This means that using a B-Tree we can have any insertion order and it will still be bushy preserving important properties.
# References

[[Binary Search Trees]]