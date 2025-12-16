
2025-04-01

Tags: [[Security]] [[Networking]] [[Software Security Evaluation]]
# Sniffing Network Traffic
Network sniffing is the process of intercepting and reading the network traffic of other network users. To sniff in a wired environment we need to have the router in promiscuous mode since otherwise the router will refuse to share the relevant information.

**Address Resolution Protocol (ARP):**
ARP is used for resolving network layer addresses into link layer addresses, this means mapping IP addresses to MAC addresses. To do this we store the correlation between each MAC address and it's IP address in a FCFS cache. One problem with this is called ARP poisoning/spoofing, and since anyone can create an ARP request we send fake requests claiming to be the gateway and hoping the devices get confused. This allows us to create a man in the middle attack and directly intercept all of their requests. We can counter this by intercepting any requests where someone else claims to be the router.
# References

