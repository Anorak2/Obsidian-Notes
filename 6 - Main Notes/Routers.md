
2025-11-20

Tags: [[3b - Classes/Networking]] [[Networking]]
# Routers
The main function of a router is to connect multiple networks and forward data packets from one network to another. A router also has multiple interfaces that each belong to a different IP network.

When a router receives an IP packet on one interface, it decides which interface it should use to forward the packet to its destination. The interface the router uses to forward the packet may either: be the network of the final destination, or it may be a network connected to another router used to reach the destination network.

**Per-router control plane:** There are individual routing components in each and every router in the control plane.

**Software Defined Networks (SDN):** Remote controller computes, installs forwarding tables in routers, Control agents (CA).  When using a SDN the behavior of the network is defined through a central server with open API's. They improve the performance of the network through virtualization and by allowing more efficient network management/more tools to network admins. 

The remote controller computers install forwarding tables in the routers, and due to OpenFlow you can "program" routers from an easy central location.

#### General Architecture
![[Pasted image 20251120001353.png]]

#### Input port functions
![[Pasted image 20251120001424.png]]

#### Longest Prefix Matching
when looking for forwarding table entry for given destination address, use longest address prefix that matches destination address

## Switching Fabrics
---
![[Pasted image 20251120001609.png]]
There are three major types of switching fabrics: Memory, bus, and interconnection networks.
- **Bus**: In a bus based router the switching speed is limited by the bus' bandwidth. in a Cisco 5600 there is a 32 gbps bus, which is good enough for an access router.
- **Interconnection Networks**: Crossbar and other interconnection nets were initially developed to connect processors in multiprocessor. This technique can exploit parallelism by fragmenting a datagram into fixed length cells on entry, switching the cells through the fabric, and then reassembling them at the end. By using multiple switching planes speeds of up to 100's of Tbps are possible 

## Queuing
---
**Input Port Queuing:** If the switch fabric is slower than input ports combined -> queuing may occur at input queues. Queuing delay and loss build up and cause the input buffer to overflow!

**Head of Line Blocking:** This is when a queued datagram at the front of the queue prevents other datagrams from moving forward.

**Output Port Queuing:** When packets arrive from the switching fabric faster than the link transmission rate buffering is required. If the buffer fills up then we have to decide which packets to drop, called a drop policy. Scheduling discipline chooses from among the the queued diagram by priority.

#### Scheduling Policies
The same idea as in cpu scheduling algorithms [[Practical CPU Scheduling Algorithms]]
- FCFS/FIFO: packets are transmitted out in the order of arrival
- Priority: header fields are used for classification, and we select the highest priority packets to send
- Round Robin: server cyclically, repeatedly scans class queues, sending one complete packet from each class (if available) in turn
- Weighted Fair Queuing: This is a generalized version of round robin where each class, i, has weight, w i, and gets weighted amount of service in each cycle

## Generalized Forwarding / OpenFlow
---
every router contains a forwarding table (aka flow table) with the "match+action abstraction" that means to match the arriving bits, and then take an action. World bending shit I know. I believe the two actions are:
- Destination-based forwarding: forwarding based on the destination IP address
- Generalized forwarding: many different header fields can determine the action, with actions such as drop/copy/modify/log packet.

**Flow:** defined by the header field values (in link-, network-, transport-layer fields)

**generalized forwarding**: simple packet-handling rules  
- match: pattern values in packet header fields  
- actions: for matched packet: drop, forward, modify, matched packet or send matched packet to controller  
- priority: disambiguate overlapping patterns  
- counters: \#bytes and \#packets

**OpenFlow:**
- OpenFlow is a protocol for control the forwarding behavior of switches/routers in a Software Defined Network (SDN) initially released by the clean slate project at Stanford.
![[Pasted image 20251120020951.png]]
![[Pasted image 20251120021033.png]]

# References
[[Network Layer Responsibilities]]
[[IP v4 Protocol]]
[[Routing Protocols]]