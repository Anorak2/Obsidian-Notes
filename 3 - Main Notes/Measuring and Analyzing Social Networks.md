
2026-04-13
 Tags: [[Information Retrieval]]
# Measuring and Analyzing Social Networks

**Basic Metrics:**
Size: Number of Nodes
Density:
$$\Delta=\frac{\sum X}{N(N-1)}$$
## Connectivity and Distance
One actor can reach another if there is a path in the graph connecting them, where a path is defined as a sequence of actors and relations that begins and ends with actors. If there is at least one path connecting every pair of actors in the graph, the graph is connected and is called a component. Two paths are independent if they only have the two end-nodes in common. If a graph has two independent paths between every pair, it is biconnected, and called a bicomponent. Similarly for three paths, four, etc.

| Name                              | Definition                                                                                       |
| --------------------------------- | ------------------------------------------------------------------------------------------------ |
| Geodesic distance (shortest path) | The number of edges in the shortest possible walk from one actor to another                      |
| Diameter                          | The largest shortest-path distance between any pair of nodes                                     |
| Maximum flow                      | The amount of different actors in the neighborhood of a source that lead to pathways to a target |
## For a given Node
For a node V there are many metrics we can talk about
Degree
- Sum of connections from or to an actor
In-degree & out-degree
- Sum of connections to/from an actor.

Centrality – how important the actor is
- Degree centrality: deg(v)/(n-1)
- Closeness centrality: average distance of one actor to all others in the network. This is related to the idea of degrees of separation
- Betweenness centrality: degree to which a vertex sits on Geodesics of other vertices. Idea is that a node that connects a lot of other nodes is an important node

Neighborhood of v
- Clustering coefficient: how close the neighbors are
- CC(v): how many edges actually occur compared to complete graph (ie, clique)

## Analysis of Networks
Reciprocity of a directed graph
- Fraction of directed edges <u, v> such that <v, u> also exists, like when you add someone as a friend, they will set you as friend too.
- In practice on several networks like Flickr and Yahoo! 360 there is a very high degree of reciprocity, 70.2% and 84% respectively. This means that in practice we can often pretend as though the graph is undirected.

Degree distribution
- The degree distributions have been shown to conform to the power law.
- For each network, the top 1% of nodes ranked by in-degree has a more than 65% overlap with the top 1% of nodes ranked by out-degree.
- Active users in social networks also tend to be popular


Small world model
- This was an experiment on delivering letters to a person from random selected people (1967, Milgram) that resulted in the  “six degrees of separation” idea
- This model is based on clustering with slight randomness; Each node knows its physical neighbors, as well as a few randomly chosen distance nodes.
-  Structural properties of the graph include
	- Clustering Coefficient: $C(p)>>C_{random}$
	- Average Geodesic distance: $L ~> L_{random}$

However there are also other models such as the Scale Free model, and structure tends to evolve slowly over time.

# References
- [[Basic Social Networks]]
- [[Graph Datastructure]]