
2025-11-20

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# ICMP
The Internet Context Management Protocol is used by hosts and routers to communicate network-level information. This is useful for a number of cases, including error reporting such as unreachable host, network, port, protocol or to echo request/reply (in the case of a ping). This  network layer is "above" IP, ICMP messages are carried in IP datagrams.

**Uses:**
- Error Reporting, if a message can't be delivered then ICMP informs the source about the failure
- Network Diagnostics such as Traceroute and ping, which uses icmp echo-reply to measure rtt time and connectivity

**Function:**
- ICMP is connectionless and doesn't require a handshake
- Messages are encapsulated withing IP datagrams
- Devices send ICMP packets for errors like unreachable hosts, expired time to lives or routing issues
![[Pasted image 20251207145132.png]]
> 0 0 echo reply (ping)  

> 3 0 dest. network unreachable  
> 3 1 dest host unreachable  
> 3 2 dest protocol unreachable  
> 3 3 dest port unreachable  
> 3 6 dest network unknown  
> 3 7 dest host unknown  

> 4 0 source quench (congestion  control - not used)  
> 8 0 echo request (ping)  
> 9 0 route advertisement  
> 10 0 router discovery  
> 11 0 TTL expired  
> 12 0 bad IP header

**Traceroute:**
To trace a route the host sends a series of UDP packets, the first with a TTL of 1 and then 2.. so on. When the datagram in the Nth set arrives at the Nth router the datagram is discarded and the router sends a source ICMP message, possibly with the name of the router and the source address.
# References
[[IP v4 Protocol]]
[[IP v6 Protocol]]
[[Routers]]
[[IP v4 Protocol]]
