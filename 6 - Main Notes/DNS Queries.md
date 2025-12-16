
2025-12-07

Tags: [[Networking]] 
# DNS Queries and Record Types
## Query Types
---


**Iterated Query**
![[Untitled.png]]
In this type each server replies with the name of the server to ask next. "I don't know this name, but ask this server"

**Recursive Query**
![[Pasted image 20250910235919.png]]
In this version all of the burden is placed on the contacted name server, and it creates an enormous load on the top layer of the hierarchy.

**Caching and time to live**
Once any server learns the request it caches the result so that it can quickly give that answer if it receives another request. These caches can be out of date so they get refreshed periodically according their time to live (TTL). One side effect is that after a change is made it may take some amount of time for the whole internet to become aware of the change.

## Record Types
---

- **A Record:** This record maps a domain name to an IPv4 address (e.g., geeksforgeeks.org to 185.199.109.153). This is the most common DNS record used to point a domain to its website's IP address.
- **CNAME Record:** The Canonical Name (CNAME) record allows you to alias one domain name to another. For example, [www.geeksforgeeks.org](https://www.geeksforgeeks.org/) can be an alias for geeksforgeeks.org.
- **MX Record:** The Mail Exchange (MX) record defines which mail servers are responsible for receiving emails for a domain. This is crucial for setting up email services.
- **TXT Record:** The Text (TXT) record stores text-based information. It is commonly used to verify domain ownership and to implement email security protocols like SPF (Sender Policy Framework) and DKIM (DomainKeys Identified Mail).
# References
[[DNS Servers]]

[[UDP]]