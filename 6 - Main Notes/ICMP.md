
2025-11-20

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# ICMP
The Internet Context Management Protocol is used by hosts and routers to communicate network-level information. This is useful for a number of cases, including error reporting such as unreachable host, network, port, protocol or to echo request/reply (in the case of a ping). This  network layer is "above" IP, ICMP messages are carried in IP datagrams.

**Trace route:**
To trace a route the host sends a series of UDP packets, the first with a TTL of 1 and then 2.. so on. When the datagram in the Nth set arrives at the Nth router the datagram is discarded and the router sends a source ICMP message, possibly with the name of the router and the source address.
# References
[[IP v4 Protocol]]
[[IP v6 Protocol]]
[[Routers]]
