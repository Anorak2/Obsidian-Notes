
2025-11-20

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# Routing Protocols
The goal of routing is to determine a "good" path from the sending host to the receiving host through a network of routers where good means: least "cost", "fastest", "least congested"

**Link Costs:** to path find properly we first need to define the costs from traveling between two nodes. Cost is defined by the network operator: it could always be 1, or inversely related to bandwidth, or inversely related to congestion
![[Pasted image 20251120024827.png]]
## Dijkstra's link-state routing algorithm
---
This is a **centralized** algorithm, with the network topology and link costs known to all nodes. in the [[OSPF and Intra IP Routing]] routing protocol this is usually done by a link-state broadcast algorithm, and all nodes have an identical and complete view of the network. Dijkstra's computes the least cost paths from one node, "source", to all other nodes which results in a **forwarding table** for that node.
![[Pasted image 20251120030612.png]]

## Distance Vector Equation
---
**Bellman-Ford Equation:**
Let $D_x(y)$: cost of least-cost path from x to y
then:
$$D_x(y)=min_v(c_{x,v}+D_v(y))$$
where min is taken over all neighbors v of x, where $c_{x,v}$ is the direct cost of a link from x to v, and $D_v(y)$ is v's least-cost-path cost to y.

**Key idea**
- from time-to-time, each node sends its own distance vector estimate to neighbors  
- when x receives new DV estimate from any neighbor, it updates its own DV using B-F equation:
$$D_x(y) \leftarrow min_v(v_{v,x}+D_v(y))$$
- under minor, natural conditions, the estimate $D_x(y)$ converge to the actual least cost $dx(y)$

![[Pasted image 20251120031206.png]]

# References
[[Network Layer Responsibilities]]
[[Routers]]
[[Graphs Shortest Path Problem - Dijkstra's]]
[[OSPF and Intra IP Routing]]
[[BGP]]
