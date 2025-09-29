
2025-09-10

Tags: [[EECS 563 - Intro to Comm Networks]]
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


**Iterated Query**
![[Untitled.png]]
In this type each server replies with the name of the server to ask next. "I don't know this name, but ask this server"

**Recursive Query**
![[Pasted image 20250910235919.png]]
In this version all of the burden is placed on the contacted name server, and it creates an enormous load on the top layer of the hierarchy.

**Caching and time to live**
Once any server learns the request it caches the result so that it can quickly give that answer if it receives another request. These caches can be out of date so they get refreshed periodically according their time to live (TTL). One side effect is that after a change is made it may take some amount of time for the whole internet to become aware of the change.
# References

