
2025-11-20

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]] 
# Network Layer Responsibilities
The network plane is responsible for transporting a segment ([[TCP]], [[UDP]], ...) from the sending host to the receiving host. The network layer is present in every device, whether hosts or routers.

**Forwarding**
- Move packets from a router's input link to the appropriate router's output link 
- Analogy:  the process of getting through a single interchange
**Routing**
- determine the route taken by a packet from the source to the destination
- Analogy: the process of planning a trip 


**Data Plane:**
- Local, per-router function
- determines how datagram arriving on router input port is forwarded to router output port
**Control Plane:**
- network-wide logic
- determines how datagram is routed among routers along end-end path from source host to destination host
- Can take either the traditional approach of routing algorithms implemented in the router or the software defined networking approach (SDN) implemented in (remote) servers.
# References
[[Routers]]