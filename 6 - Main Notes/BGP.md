
2025-11-20

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# BGP
Border Gateway Protocol is the de-facto inter-domain routing protocol that holds the internet together. allows AS to advertise its existence, and the destinations it can reach, to rest of Internet: “I am here, here is who I can reach, and how”  BGP provides each AS a means to:  
- eBGP: obtain AS reachability information from neighboring ASes 
- iBGP: propagate reachability information to all AS‐internal routers.  
- determine “good” routes to other networks based on reachability information and policy

## Basics
---
BGP session: advertising paths to different destination network prefixes (BGP is a “path vector” protocol)
![[Pasted image 20251120034008.png]]

**Hot Potato Routing**
![[Pasted image 20251120034226.png]]
2d learns (via iBGP) it can route to X via 2a or 2c  
- hot potato routing: choose local gateway that has least intra‐domain  cost (e.g., 2d chooses 2a, even though more AS hops to X): don’t worry about inter‐domain cost!

**BGP Route Selection**
router may learn about more than one route to destination AS, selects route based on:  
1. local preference value attribute: policy decision  
2. shortest AS‐PATH  
3. closest NEXT‐HOP router: hot potato routing  
4. additional criteria
## Why have different Inter vs Intra AS routing
policy:  
- inter‐AS: admin wants control over how its traffic routed, who routes through its network  
- intra‐AS: single admin, so policy less of an issue  
scale:  
- hierarchical routing saves table size, reduced update traffic  
performance:  
- intra‐AS: can focus on performance  
- inter‐AS: policy dominates over performance

# References
[[Network Layer Responsibilities]]
[[Routers]]
[[Graphs Shortest Path Problem - Dijkstra's]]
[[OSPF and Intra IP Routing]]
[[BGP]]
