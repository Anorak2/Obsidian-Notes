
[[Basic Networking Terminology]]
[[OSI Model]]
# Networking
## 2 - Application Layer
---
[[SMTP]]
[[Alternative Mail Access Protocols]]
[[HTTP]]
[[HTTP]]
[[P2P Applications*]]
[[Ports*]]
[[Web Sockets*]]

[[DNS Servers]]
[[DNS Queries]]

## 3 - Transport Layer Protocols
---
[[Ports*]]

[[Reliable Data Transfer (RDT)]]
[[Pipelined Protocols]]
[[TCP]]
[[UDP]]
[[Network Congestion Control]]

## 4 - Network Layer - Data Plane
---
[[Network Layer Responsibilities]]
[[Routers]]
[[Network Address Translation (NAT)]]

[[IPv4 Protocol]]
[[IPv6 Protocol]]

[[DHCP]]
[[Network IP assignment]]
## 5 - Network Layer - Control Plane
---
[[OSPF and Intra IP Routing]]
[[Border Gateway Protocol (BGP)]]
[[Routing Protocols]]
[[ICMP]]

## 6 - Link Layer
---
[[Link Layer Error Detection]]
[[MAC Addresses*]]
[[LAN's*]]
[[ARP]]
[[Ethernet*]]

## 7 - Physical Layer
---
[[Wireless Networks]]
[[LAN's*]]
[[Network Multiple Access Protocols]]
[[Interconnection networks]]
# Network Security
- [[Network + Port scanning (Nmap and Nessus)]]
- [[Sniffing Network Traffic]]
- [[Denial of Service Attacks and DDoS Attacks]]
- [[ARP Attacks*]]
- [[OSPF attack and defenses*]]
- [[BGP Security]]
- [[DNS Security]]
- [[TCP Security]]

Wifi:
- [[Wireless Network Cracking (WEP)]]
- [[Wireless Network Cracking (WPA & WPA2)]]
- [[WPA 3]]

- [[Firewalls*]]

Protocols
– IP (and ICMP)
– OSPF and BGP
– TCP and UDP
– DNS
■ Security problems
– Lack of authentication – spoof IP address
– Lack of integrity – spoof header fields and payload
– Lack of confidentiality
– Protocol asymmetries

Given an attack, you should know:
– Which layer it exploits
– Which protocol it exploits
– Which vulnerability it exploits
– Root causes of the vulnerabilities
– Its consequences
– Countermeasure or possible strategies to defend against it
– Limitations of the defense

Network-layer attack
– ARP attacks
– OSPF attacks
– BGP attacks, e.g., prefix hijacking
– DNS attacks, e.g., cache poisoning
■ TCP-layer layer
– Off-path attacks
■ DoS attacks
– Reflection attacks
– Amplification attacks

Mitigation methods
– Filtering
■ Patching existing protocols
– RPKI and BGPSec
– DNSSEC

Lectures 3-7