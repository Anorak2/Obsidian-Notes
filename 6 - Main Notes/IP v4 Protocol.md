
2025-11-20

Tags: [[3b - Classes/Networking]] [[Networking]]
# IP v4 Protocol
![[Pasted image 20251120003312.png]]


**Addressing:**
In IP v4 there is a 32 bit identifier associated with each host or [[Routers|router]] interface that is seen in the source IP address and the destination IP address. 

**Subnets**
A subnet is a set of device interfaces that can reach eachother without passing through an in-between router. IP addresses have a structure where devices on the same subnet have the same high order bits and the low order bits denote the host address.

#### CIDR
CIDR, or Classless Internet Domain Routing, allows for a subnet portion of arbitrary length. This is possible because with the address format `a.b.c.d/x` X is the number of bits in the subnet portion of the address.

**Special Addresses**
Within each subnet two IP addresses are special and reserved.  
- Network Address: Identifies the subnet itself.  
- Usage: Used in routing tables to represent the entire network.  
- ex: For subnet 223.1.2.0/24, the network address is 223.1.2.0.

Broadcast address: Special IP 255.255.255.255.  
- A host sends a datagram with destination address 255.255.255.255 and the message is delivered to all hosts on the same subnet
## Other
#### Fragmentation/Reassembly
The largest size (in bytes) that a single packet or frame can be sent over without being fragmented is called the **MTU**. 
Fragmentation allows for:
1. Transport layer protocols to be independent of the underlying network architecture, reducing overheads
2. IP and higher layer protocols to work across variable and diverse network paths and mediums (not everyone has expensive routers etc).

**Concerns**
- Fragmentation really complicates things for both the routers and for the end systems
- DoS attacks are possible. One example is the Jolt2 attack which sends a stream of small fragments to the target host, none with an offset of 0.
- [[IP v6 Protocol]] has removed fragmentation because of this

**Don't Fragment Bit**
- if we don't want to deal with any fragmentation problems then we can set the DF bit so that no router is "allowed" to fragment it.
- If the router can't deliver a packet and can't fragment it then it is supposed to return a "Destination Unreachable Message"

#### Multicast
IP multicast is a way to efficiently deliver packets to multiple recipients at the same time, with the idea of sending to all recipients (broadcast) rather than a single recipient (unicast).

Any address in the range from 224.0.0.0 to 233.255.255.255 is specifically reserved for multicast.

# References
[[Routers]]

[[Denial of Service Attacks and DDoS Attacks]]
