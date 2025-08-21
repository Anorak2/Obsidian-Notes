Status: 

Tags: [[Algorithms]] 
# Dijkstra's Algorithm

This is a [[Graphs|Graph]] Problem where we need to find the shortest path between two points, but with a twist since now we require that edges are weighted instead of unweighted. This is a problem since our old versions of algorithms like BFS now no longer find the shortest path. **Given that each path is non-negative, Dijkstra's algorithm is guaranteed to give the optimal path**.


**Dijkstra's Algorithm**
Dijkstra's algorithm works by taking a **best** first search by taking the edge with the lowest weight each time, and similarly to DFS backtracking if we reach a dead end.

**Invariants**
- edgeTo(V) is the best known predecessor to v
- distTo(V) is the best known total distance from the source to V
- PQ contains all unvisited vertices in order to distTo

**Important Properties**
- Always visits vertices in order of total distance from the source
- Relaxation always fails on visited vertices

**Algorithm**
1. Mark the source node with a current distance of 0 and the rest with infinity.
2. Move the current node to the closest neighbor
3. For each neighbor, N of the current node adds the current distance of the adjacent node with the weight of the edge connecting 0->1. If it is smaller than the current distance of Node, set it as the new current distance of N.
4. Mark the current node 1 as visited.
5. Go to step 2 if there are any nodes are unvisited.

# References
[[Graphs]]