
2025-09-10

Tags: [[Networking]]
# DNS Servers
DNS, or Domain Name System, is a distributed database that exists as a hierarchy of name servers that allows for the internet to convert a name like www.jellyatoll.xyz into an IP address like ```127.0.0.1```. 

![[Pasted image 20250910234410.png]]

**Root Name Servers**
These servers are incredibly important to the internet, they serve as the top level in the DNS system. These servers return the appropriate authoritative name server for the appropriate domain. 

**Top Level Domain Servers (TLD)**
TLD servers are responsible for all .com, .edu, .org, .net, .edu, and all top level country domains, and they are in charge of routing to all websites inside of their domain.

**Authoritative DNS servers**
This server belongs to an organization and it is responsible for providing authoritative hostname to IP mappings for that organizations named hosts.

**Local DNS Servers**
These don't belong in any particular place in the hierarchy, and it is maintained by each ISP. When a host makes a DNS query, a query is sent to the local DNS server that has a cache of recent name to address pairs, although this cache can be out of date.

# References
[[IP v4 Protocol]]
[[IP v6 Protocol]]

