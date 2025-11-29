
2025-11-20

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# IP v6 Protocol
![[Pasted image 20251120014033.png]]
The IPv6 Protocol was designed to fix the problems with IPv4 by eliminating unnecessary headers and by increasing the address space enormously. When compared to IPv4 IPv6 is missing:
- no checksum (to speed processing at routers)  
- no fragmentation/reassembly (sender may perform fragmentation at the source; but IPv6 router does not do it! It sends ICMP packet if datagram is too large. )  
- no options (available as upper-layer, next-header protocol at router)

#### Transition from IPv4 to IPv6 + Tunneling
Since not all routers can be upgraded simultaneously we need to have both standards exist for some time until all can be upgraded. To fix this we introduce **tunneling** which is where we enclose an IPv6 datagram inside of an IPv4 packet so that we can be compatible with older routers.

This works through 6-4 tunneling (RFC 3056) where packets are automatically encapsulated if the next hop isn't IPv6 capable. Routers also don't discover IPv6 capabilities dynamically, instead protocols like OSPF and BGP4 advertise IPv6 routers explicitly.
# References
[[IP v4 Protocol]]

[[OSPF and Intra IP Routing]]

[[BGP]]