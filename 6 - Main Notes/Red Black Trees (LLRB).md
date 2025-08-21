Status:

Tags: [[Data Structures]]
# Red Black Trees
Red Black trees are, fundamentally, the same as [[B-Trees]] and therefore also very similar to [[Binary Search Trees]]. However, red black trees fix a lot of the implementation problems and performance problems that [[B-Trees]] have.

| Height      | Contains    | Insert      | Delete                         |
| ----------- | ----------- | ----------- | ------------------------------ |
| O($\log n$) | O($\log n$) | O($\log n$) | Complicated, apparently boring |
**Main Idea**
Since we don't want to have 3 or 4 nodes, what we can do is instead create a "dummy" node, but that really isn't very elegant. Instead, we can use "glue" links, which we usually mark in red hence the name. What is cool, is that the tree we have created is actually still a BST since the red links don't "do" anything, they are just more convenient to think of that way. We also call these trees left leaning red black trees, since if there is a red link we put it on the left side by convention, otherwise it would be a RLRB.

This means that we can search an LLRB in the exact same way we would a BST.

**How do we build an LLRB?**
To build one is actually kind of easy, all we need to do is insert into it as we usually would and then use rotations to maintain a 1-1 mapping.

**One** - No children
If we are adding to a node with no children we **always** start by adding a red node first.
**Two** - Temporary 4-node
If we already have a node with a child, we can start by adding a **temporary** 4-node, a red link to the right. 
**Three** - double left insert
If have a double insertion on the left, then we can [[Tree Rotation|rotate]] the top node and get a temporary 4-node.
![[Pasted image 20241128020244.png]]

**Four** - Splitting 4-nodes
If we have a temporary 4-node then we can split it by flipping the colors of all edges touching a node, in the above case S. What is really cool about this is that the structure  isn't changing, just how we think about it. If we get an invalid tree from flipping this color, say by having a red node on the right side, we can fix this by rotating the node who has a right red link to their child.
![[Pasted image 20241128020526.png]]



**Useful Properties**
- No node can have 2 red links since then it would be the same as a 4-node which we don't allow with 2-3 trees
- Every path from the root to the leaf has the same number of black nodes, and therefore LLRBs are balanced

# References
[[B-Trees]]

[[Tree]]