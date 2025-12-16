
2025-01-30

Tags: [[Networking]] [[Software Security Evaluation]]
##  Basic Networking Terminology

To interact with the internet you need a N.I.C. card, short for network interface card. This can plug into an ethernet cable, or an RJ45 connection

- MAC address, this is short for a Media Access Controller address and it is a unique ID assigned to network interfaces. It looks like 00:00:00:11:11:11 where the 0's are a manufacturer and the 1's are the unique ID
- IP address, or internet protocol address. It's a label assigned to devices that use the internet protocol and mainly for identification between the host and network interface and for location addressing. There are two types, IP v.4 (32 bit) and IP v.6 (128 bit)
- IP vs MAC, a MAC address generally stays fixed and an IP address changes as the devices moves from one network to another. Generally speaking though the MAC address is used for the hardware implementation and the IP is used for the software implementation.
- Ports; Ports can be either physical or virtual and they allow for in the case of physical connecting cables, or used for virtual ports for software to use the same hardware without interfering. (16 bit is 0-65535)
- **Routing** is determining the path that packets between two nodes follow
- **Forwarding** is advancing packets along their route
- **Address types**
- **Broadcast types** Unicast is when we have a one to one connection of traffic, a multicast which is one to many operation, and lastly a broadcast which is a one to all operation
- **Protocol** A: Hi   B : Hi,   A: what time is it?   B: 10 am. This is the same as a TCP con request, TCP con response, GET request, and then sending a file in response. 

![[Pasted image 20250130232958.png]]


![[Pasted image 20250130233617.png]]

![[Pasted image 20250424145106.png]]


## Structure
The basic building blocks of the network are:
- nodes or edges; and this can be end systems like computers, but also switches and routers
- links: optical cable, coax cable. these can be point to point or multiple access

**Network**
A network can be defined as two or more nodes connected by a link. The end nodes are called hosts, and internal nodes are switches and routers with the main requirement of providing connectivity.

A **router** is a specialized node that connects between networks
# References


