tags: [[Algorithms]]
# Kruskal's Algorithm

**Algorithm**
This algorithm works by starting with the edges with the lowest weights first, and it is very important that they don't need to be connected. We keep doing this unless adding an edge creates a cycle, and this is because we would be adding an unnecessary edge (it also would no longer be a tree) and since we started by adding the lowest weights first it must have a higher weight.


## References

[[Graphs|Graph]] 

[[Graphs Shortest Path Problem - Dijkstra's|Dijkstra's]] 

[[Graphs Spanning Tree and Min Spanning Tree|Prim's Algorithm]]