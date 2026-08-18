
2026-05-11

Tags: [[Web]] [[Networking]] [[Networking]]
# Internet Censorship
>“Censorship, the suppression of words, images, or ideas that are "offensive," happens whenever some people succeed in imposing their personal political or moral values on others. Censorship can be carried out by the government as well as private pressure groups. Censorship by the government is unconstitutional.”
> The ACLU

Censorship is seen in many forms, some include
- shutting down the internet
- Throttling of certain services
- Removal of "offensive" content

## Network Censors
![[Pasted image 20260511230923.png]]
Primary techniques: network-level blocking
- Network censors – devices positioned on the communication path
- Observe or examine traffic: Identify by IP address, hostname, URL, keywords, deep packet inspection, etc.
- They operate in real time inside the network. They can lock or disrupt connections, such as dropping packets, modifying or injecting packets such as forging TCP RST packets or DNS responses, or degrade service quality by throttling

## Censorship Techniques
**In Path: IP Blocking**
Easy to implement and efficient. But, you need to know the IP, high processing requirement O(N) for list scan, high collateral damage, blacklist can be long, easy to detect an evade (brittle).

**In Path: BGP Blocking**

**In Path: DNS manipulation**
Easy to implement and efficient. But, you need to know the domains, cannot drop packets, high collateral damage, blacklist can be long, less easy to detect.

**In Path: Application Layer Blocking**
![[Pasted image 20260511231921.png]]
This approach is flexible and harder to evade, yet it is also slow to implement and can be detected.

**On-Path Censor: TCP RST**
![[Pasted image 20260511232917.png]]
This is how China's great firewall operates and it's important to note that it isn't just TCP they will interfere with. They will also try to interfere with UDP or other connections however they can

 **Active Probing:** 
 Censors want to determine if a circumvention tool is in use, censor can identify suspicious connection (e.g., unusual TLS fingerprint).  It replays the initial bytes of the client to the server. Based on the received response, it detects and blocks the circumvention server.

This also means if you are circumventing your app must be “probe-resistant.” Distinguish legitimate clients from probes without breaking usability.

**Active Probing with TOR**
- Identify a real Tor user (using DPI)
- Follow the user connecting to a bridge node
- Try to connect to the suspected node by initiating TLS handshake
- If success, confirm the node is a Tor bridge node. Then, block all connections to that node.

## Circumvention
Common anti-censorship tools
- VPN and SSH, but VPN websites and traffic can also be blocked
- Various proxies like G-pass and Ultrasurf
- Censorship resistant communication software like TOR, anonymizer, and the freenet project

**It's a cat and mouse game**
![[Pasted image 20260511233509.png]]


**Bridge Nodes**
- Use Bridge Nodes, not publicly known
- Tor Browser
- Or send email to bridges@bridges.torproject.org

**Reflection networking**
![[Pasted image 20260511234257.png]]
- Point is to transform the Tor traffic flow between the client and the bridge into an innocent-looking traffic

**Parroting: imitating non-censored protocols**
![[Pasted image 20260511234324.png]]
Unobservability by imitation is fundamentally flawed! The problem is imitation requirements are too difficult/costly to meet, and partial imitation is worse than no imitation. It is easier to detect parrot traffic than Tor traffic.

**Pluggable Transport (PT)**
- PT is to transform the Tor traffic flow between the client and the bridge into an innocent-looking traffic
- obfs4 adds another layer encryption between client and bridge, making Tor traffic unrecognizable
- meek first connects to a real HTTPS web server such as CDN and then connects to the actual bridge
# References
- [[General Anonymous Communication]]