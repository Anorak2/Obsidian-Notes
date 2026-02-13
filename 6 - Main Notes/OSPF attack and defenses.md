
2026-02-11

Tags: [[Networking and Network Security]]
# OSPF attack and defenses
Open Shortest Path First is a networking protocol that is inherently safer than some other protocols like RIP. To do this it requires bidirectional links advertised by both ends and cryptographic authentication using `HMAC-sha`. It also has a fight back mechanism so that when a router receives an LSA (link state advertisement) of its own but newer than its last instance, it sends a new LSA to cancel out the false one.
## OSPF Problems and Attacks


## Defenses
- Reverse path forwarding
	- Check for spoofed source IP addresses at boundary of domain
-  Fight-back provides hints of attack
	- Alert admin to analyze the cause of fight-back
- For remote false adjacency attack, diverse keys on different networks
- For disguised LSA, randomize OSPF LSA sequence numbers
- For persistent poisoning, revise fight-back mechanism
	- CVE-2013-0149 → vendor patches

# References
- [[Routing Protocols]]

