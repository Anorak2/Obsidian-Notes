
2026-03-26

Tags: [[Networking]] [[Network Security]]
# Virtual Private Networks (VPN)
A virtual private private network is a way to tunnel your traffic to a different network so that it is as if your network traffic originated there. This solves two fundamental problems; how to protect network traffic when the user is on an insecure LAN, and how does an organization connect sites that are geographically separated? A VPN solves this by providing secure access to private network over public links with Confidentiality,  Integrity, Mutual authentication. VPN's are also easy to implement with SSL, SOCKS, or VPN software
## Types of VPNs
![[Pasted image 20260326235713.png]]

Usually I have seen the client to gateway VPN rather than the gateway to gateway.

## Tunneling Protocols
There are a number of VPN tunneling protocols, including IPsec, SSH Tunneling, OpenVPN which tunnels traffic via SSL/TLS connections, Point-to-Point Tunneling Protocol (`PPTP`) which uses Control channel (TCP) and Data channel (`GRE`).

**General**
A tunneling protocol transfers a packet between two disconnected networks by encapsulating a packet inside of another packet, and this can then be unpacked at the destination. One issue is that many tunneling protocols don't support encryption by default, and some servers are still vulnerable despite changes like SSH over telnet. In 2025 a study found four million vulnerable hosts, these hosts are vulnerable to IPIP spoofing attacks, temporal leasing attacks, and Ping-Pong amplification attacks.

## Pros/Cons
Advantages
- Easy to configure
- Many services available
- Doesn't require the receiver’s participation
Disadvantages
- Proxy is a trusted third party that may not be fully trusted (proxy may sell/release its logs, or blackmail sender)
- Anonymity relies on the threat model (where is Eve)


# References
- [[TCP]]
- [[SSL*]]