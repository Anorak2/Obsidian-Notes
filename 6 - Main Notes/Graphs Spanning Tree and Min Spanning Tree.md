Tags: [[Graphs]] [[Algorithms]]

# Spanning Tree and Minimum Spanning Tree

Given an undirected graph, a spanning tree T is a sub-graph of G, where T:
- Is Connected (makes it a tree)
- Is acyclic (makes it a tree)
- Includes all of the vertices. (Spanning)

**Minimum Spanning Tree**
A minimum spanning tree is a spanning tree with the minimum total weight, and example of why this is awesome is this covers examples such as connecting buildings with power lines.

**Cutting**
A cut is when we just split the nodes into two sets, and it can be arbitrary. Cuts are useful because for any cut, there is a minimum weight crossing edge inside of the cut

**Prim's Algorithm**
We start from an arbitrary starting node.
- Repeatedly add the shortest edge that has one node inside of the MST under construction
- Repeat until V-1 edges

This algorithm works but if we do this naturally then our implementation is pretty inefficient. Instead what we do is we can store the distance to a node, and each time we can relax all of the other nodes after finding the lowest. What is interesting is that Prim's and [[Graphs Shortest Path Problem - Dijkstra's|Dijkstra's]] algorithms are actually the same except that Dijkstra's considers distance from the source and Prim's distance from the tree.
# References

[[Graphs]]

[[Graphs Shortest Path Problem - Dijkstra's]]