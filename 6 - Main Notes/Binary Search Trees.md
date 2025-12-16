Tags: [[Data Structures]]
# Binary Search Trees

Binary search trees are pretty well covered but refreshers never hurt. The idea of a BST is that we have a bunch of things, as long as they can be compared, and we want to search through our set and find if an item is in it. We can search efficiently using a [[Tree]]. Also, although the worst case is O(n) when dealing with randomized data we usually generate bushy trees meaning that for a lot of cases we will get O($\log n$) 

|            | Contains    | Insert      | Delete          |
| ---------- | ----------- | ----------- | --------------- |
| When Bushy | O($\log n$) | O($\log n$) | O($\log n$)<br> |
| Worst Case | O(n)        | O(n)        | O(n)            |
**Ordering**
Ordering must be both transitive and anti-symmetric, which given p and q means
- anti-symmetric: p ≺ q XOR q ≺ p
- transitive: p ≺ q and q ≺ r implies q ≺ r

**Search**
Given this structure, searching is actually pretty easy. The pseudocode looks like:
if t.key == None return false
if search_key = t.key we return true
if search_key ≺ T.key, search T.left
If T.key ≺ search_key, search T.right

**Insert** 
We start by searching for a key, and if we find it we do nothing. If we don't find it then create a new node and make sure there is the correct edge connecting it

**Deleting**
Deleting unfortunately is a bit more complicated, but the idea is that there are three possible cases that we have to account for. If a node has no children, one child, or two children.

No children:
This case is trivial since we don't need to update any nodes

One child:
If this is the case then we can just have the child replace the position of the parent node

Two children:
This case is definitely a little harder, but if you remember the properties of a BST then what we need is a node that is bigger than everything on the left side of the parent, but larger then everything on the right side of the parent. This actually isn't too hard to do, we just need to go left once, and then right until we can't anymore and by definition this node is larger then every other node on the left side yet still smaller then the right nodes. This same idea also works the other way around for the right side. We can then just take this node we found (which can only have one or 0 children) and replace the node that we were deleting.

# References

[[Tree]]