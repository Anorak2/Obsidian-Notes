
2025-11-20

Tags: [[3b - Classes/Networking]] [[Networking]]
# OSPF
Often in the other networking layer steps we've been assuming relatively flat, ideal networks. In practice though we can't store billions of connections in every router. Instead we aggregate routers into "autonomous-zones" or domains, this includes Google, Facebook, Apple, etc where each AS is given an Autonomous Systems Number. In north America this number is given by ARIN (American Registry for Internet Numbers).

**OSPF:**
Open Shortest Path First routing, described in RFC `2328`, is classic link-state where each router floods OSPF link-state advertisements to all other routers in the entire AS. multiple link costs metrics possible: bandwidth, delay each router has full topology, uses Dijkstra’s algorithm to compute the forwarding table. For security reasons all OSPF messages are authenticated to prevent malicious intrusion.
![[Pasted image 20251120032954.png]]

## Internet Layers
---
Often divided into four:
- Autonomous Systems: Aggregates routers by ownership
- Point of Presence: supports geo-physically aware topology analysis
- Router: refers to the set of routers that transfer and route
- IP: addresses an attachment point (interface) of a device on the Internet
## Intra-AS Routing
---
All routers in the same autonomous zone must run the same intra-domain protocol, though routers in a different AS can run different intra-domain protocols, hence the name autonomous zone. Each AS has **gateway routers** that is at the "edge" of it's autonomous zone and has links to routers in other AS's

## Inter-AS Routing
This is routing among autonomous zones. The forwarding table has to be configured by inter and intra AS routing algorithms. intra-AS routing determine entries for destinations within AS, inter-AS & intra-AS determine entries for external destinations. 


# References

