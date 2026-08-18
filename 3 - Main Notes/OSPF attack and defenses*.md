
2026-02-11

Tags: [[Networking]] [[Networking]]
# OSPF attack and defenses
Open Shortest Path First is a networking protocol that is inherently safer than some other protocols like RIP. To do this it requires bidirectional links advertised by both ends and cryptographic authentication using `HMAC-sha`. It also has a fight back mechanism so that when a router receives an LSA (link state advertisement) of its own but newer than its last instance, it sends a new LSA to cancel out the false one.
## OSPF Problems and Attacks
Attackers can bypass authentication
- NULL authentication: authentication is optional
- Text-based password: attacker can sniff OSPF packets to obtain the password
Compromised routers
- Several vulnerabilities reported: CVE-2009-2865, CVE-2010-0581, CVE-2010-0580, CVE-2013-0149, CVE-2017-6770
- The goal is to forge LSA: the victim router flush its routing table and propagate the crafted bogus LSA.

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
- [[Packet Routing Protocols]]
- [[OSPF and Intra IP Routing]]
