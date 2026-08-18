
2026-07-13

Tags: [[Data Systems]] [[Databases]] [[Data]]
# Graph Database Model
The graph data model excels at modeling highly connected data, and data with many different forms of relationships or complex connections between nodes. A graph is simple composed of nodes which are arbitrary points, and vertices which are able to connect these nodes. Common examples of use-cases include social graphs, the connections between web pages, and road networks. There are many useful algorithms that can operate on these graphs, including Dijkstra's algorithm, A*, and many more.

## Property Graph Model
In this model each node is composed of:
-  a unique identifier
- a set of outgoing edges
- a set of incoming edges
- a collection of properties (key/value pairs)

Each edge is composed of:
- a unique identifier
- a node the edge starts at
- a node the edge ends at
- a description, or label, that describes the relationship
- a collection of properties (key/value)

Any node can be connected to any other node, there's no schema the data store enforces. These databases also make it easy, and more importantly efficient, to find any neighboring nodes. Multiple different types of data can be stored on the same graph using different types of edges between nodes.

### Cypher Example
Cypher is a declarative language for querying property graphs, created for the Neo4j graph database.

```Cypher
MATCH
(person) -[:BORN_IN]-> () -[:WITHIN*0..]-> (us:Location {name:'United States'}),
(person) -[:LIVES_IN]-> () -[:WITHIN*0..]-> (eu:Location {name:'Europe'})
RETURN person.name
```
The query means to find a node, which is called person, that matches two different conditions. First that person has an outgoing edge `born_in` that eventually is able to resolve to the `United States`. Second, that same person node must also have an edge `lives_in` that resolves to `Europe`. Then it returns that person's name.
## Triple Store Model


# References
- [[Relational Database Model]]
- [[Graph Datastructure]]
- [[A* Search Algorithm*]]
- [[Dijkstra's Algorithm]]
