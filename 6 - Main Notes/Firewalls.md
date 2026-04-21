
2025-04-29

Tags: [[Software Security]] [[Networking and Network Security]] 
# Firewalls
Firewalls are a fundamental part of network security, and realizes access control over traffic. They may also have other capabilities like NAT, logging, flagging (intrusion detection), authentication / VPN, quality of service `QoS`. Notably firewalls can't stop malicious insiders, attacks that don't go through it, protect against novel threats, fully protect against viruses.

## Policies
Firewalls filter traffic based on policies that evaluate to a binary accept or deny. An example is “HTTP should be allowed to any external host, but inbound only to web-server.” Since a policy may not apply, we set a default policy of either Blacklisting or Whitelisting. Blacklisting specifies connections that are explicitly banned, which is a less secure approach since we may forget or now know how to block attackers. Whitelisting blocks all connections by default, this is more secure but may break some functionality. Most Operating Systems default accept but most organizations network deny by default.

**Rule Order**
The order our rules our in is actually very important for most firewall policies, since they are monotonic the firewall will go down the list in order until it finds a match. By doing this we can express very complex series of rules.

**Stateless**
Each packet is considered independently, can be difficult since TCP for example is part of an established session. If we are doing stateless we can work around this limitation, for example by allowing inbound packets with the ACK bit set. The bigger issues are UDP, ICMP, RFC, FTP and more each with different reasons.

Advantages:
- much faster processing of packets

Disadvantages:
1. more complex rule specification
2. less secure (e.g., ACK scanning)
3. difficult to handle multi-port protocols such as FTP

Use cases:
- Simple scenarios such as strict configuration and ingress/egress filtering

**Stateful**
Allows consideration of the historical context. This approach requires per-connection state in the firewall, and when a packet is sent out it's recorded in memory. Also associates in-bound packet with state created by out-bound packet, fixing an issue with stateless. 

Advantages:
- Simple rule specification, allowing more complex policies
- More secure due to added context
- can handle FTP (sometimes)
Disadvantages:
- Slower at processing packets
- Still can't handle dynamically negotiated port numbers or higher level protocol semantics 
## DMZ
![[Pasted image 20260326101229.png]]
Also called a screened subnet or perimeter network. A demilitarized zone is a semi-trusted area distinct from the trusted intranet, but also able to access the internet. This is often done for public facing servers.

When implementing you can have a 2 layer firewall such as internet > DMZ > trusted intranet, or a "three legged" firewall where there is also a firewall between the DMZ and intranet.

## Protocols
**UPnP,  Universal Plug and Play**
- Home routers use it to enable device discovery and NAT traversal
- “I can be reached by external host on port 12345”
- Punch holes in FW
- No authentication, allowing for malware, flash/XSS, or RPC

**Circuit level gateways / Circuit level proxy**
- Sets up two TCP connections with two endpoints and relays packets from one connection to the other
- Can be a stand-alone system or in an application FW
For example, SOCKS Proxy
- Socket Secure (SOCKS) is a protocol for generic forwarding of packets through a proxy
- It support HTTP, FTP, SMTP, POP3, NNTP, etc.
ex:
```javascript
ssh -D 12345 sshserver.com
chrome - - proxy-server = `socks://localhost:12345’
```

**Application level Proxy / Forwarding**
It relays application-level traffic
- Similar to circuit-level proxy, but less generic
- The proxy code is for a specific application (or specific features of the application)
- E.g., recent “Web application FW” detecting XSS, SQL injection, …
Can do:
- Application-specific filtering
	- E.g., SMTP doing spam filtering, phishing detection, …
- Begin to overlap with IDS
## Issues and Limitations
**Practical Issues**
- Network layer firewalls are dominant
- DMZs allow multi-tiered firewalling
- Tools are widely available and mature
- Personal firewalls gaining popularity

**Issues**
- Network perimeters not quite as clear as before
	- E.g., telecommuters, VPNs, wireless
- Every access point must be protected
- Hard to debug, maintain consistency and correctness
- Often seen by non-security personnel as impediment
	- E.g., Just open port X so I can use my wonder widget

**Limitations**
- Most network traffic now transmitted over HTTP
- Does not help once the attacker is inside the network
	- E.g., laptop or mobile device compromised on another network
	- E.g., Internal user visits a compromised Website
- Advanced Persistent Threats (APTs) often move laterally within the network to avoid firewalls
## iptables
The iptables firewall uses tables to organize its rules, and within each table, rules are organized within separate chains. A chain is a checklist of firewall rules; at each stage packets either get dropped or advance towards next chain,


**Chains:**
This is an interface with the net-filter packet filtering framework iptables interfaces with the netfilter packet filtering framework
- INPUT: if packet is destined for this host
	- Triggered by the NF_IP_LOCAL_IN hook
- FORWARD: if packet is destined for another network interface
	- Triggered by the NF_IP_FORWARD hook
- OUTPUT: outgoing packets
	- Triggered by the NF_IP_LOCAL_OUT hook
- `PREROUTING` and `POSTROUTING`
These first three make up the filter table

**Rule Parameters**
There's a lot of things you can match on, including either specific IPs or IP address range / net mask for sender and receiver. The protocol of packet, packet fragmentation flags, incoming/outgoing interface. There are also per protocol flags like for TCP SYN bit or TCP flags

**Targets**
A target is the action being triggered, it defines what to do with the packet at this time:
- ACCEPT/DROP
- REJECT drops and returns error packet
- QUEUE for user-space application
- LOG any packet that matches
- RETURN enables packet to return to previous chain
# References
- [[Intrusion Detection Systems (IDS)]]
- [[TCP]]
- [[ICMP]]
- [[Intrusion Detection Systems (IDS)]]
- [How to use iptables](https://www.netfilter.org/documentation/HOWTO/packet-filtering-HOWTO.html)