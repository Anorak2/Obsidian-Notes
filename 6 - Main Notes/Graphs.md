Tags: [[Data Structures]]
# Graphs

**Definition**
A graph consists of a set of nodes, and a set of edges which each contain two or more nodes. Something to remember is that all [[Tree|trees]] are specialized versions of graphs.

| Idea             | AddEdges(s,t) | For(w : adj(v))              | print()        | hasEdge(s,t)          | space used     |
| ---------------- | ------------- | ---------------------------- | -------------- | --------------------- | -------------- |
| adjacency matrix | $\Theta (1)$  | $\Theta (V)$                 | $\Theta (V^2)$ | $\Theta (1)$          | $\Theta (V^2)$ |
| list of edges    | $\Theta (1)$  | $\Theta (E)$                 | $\Theta (E)$   | $\Theta (E)$          | $\Theta (E)$   |
| adjacency list   | $\Theta (1)$  | $\Theta (1)$ to $\Theta (V)$ | $\Theta (V+E)$ | $\Theta (degree (v))$ | $\Theta (E+V)$ |
 
**Simple Graph**
A simple graph is a graph with:
- No edges that connect a node to itself, loops
- No two edges that connect to the same vertices, parallel edges

**S-T Connectivity**
This is a problem where given two nodes, S and T, is there a path between those two nodes. There are a couple things that make this more complicated, like making accidental loops. A simple way to solve this problem would be to do a depth first search, see below, through the graph and return true if we ever end up on the node we are looking for and false if we don't.

**S-T Shortest Path**
This is the idea where we need to find the shortest path between a node S and every reachable vertex. Using an adjacency list,and a breadth first path implementation the efficiency with an adjacency list is $\Theta(V+E)$ time and $\Theta(V)$ space. 

**Depth First Traversal and Breadth First Traversal.**
The main idea behind depth first traversal is exploring the sub-graph of each node before moving on to its neighbor. Whats cool is since we're doing traversal it can easily be applied to a bunch of algorithms. Breadth first traversal is similar to depth first, and both are comparable, but rather than travel forward until we can't and then backtracking we visit all nodes of a certain distance away.

Both are correct, and both give similar results (including runtime) although BFS is a 2-1 deal since not only do we get the path but it is guaranteed to be the shortest. In terms of space complexity DFS is worse for highly spindly graphs since it fills up the call stack, and BFS is worse for bushy graphs since the queue can get very large.

**Representations**
As we say with [[Tree|trees]], how we model our data-structures can have large impacts on the performance of certain operations. There's a couple of ways to model a graph, with one way being an adjacency matrix, seen below

![[Pasted image 20241130171738.png]] 
An alternative approach would be to use a collection of edges, ex: {(0,1),(1,2),(2,3)}
Or another approach would be to use adjacency lists, 
[0] -> [1]
[1] -> [0,2]
[2] -> [1,3]
[3] -> [2]

# References
[[Tree]]

[[Singly Linked List]]