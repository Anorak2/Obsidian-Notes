
2026-02-10

Tags: [[Networking and Network Security]] [[Software Security]]
# ARP Attacks
ARP problems:
- Stateless: ARP accepts replies without requests
- Hosts cache ARP replies in ARP table for a (short) period of time
- Each ARP response overwrites the previous entry and the last response wins
In ARP spoofing, attacker forges an ARP response
- a.k.a. ARP Poisoning or ARP Flooding
- Attacker claims his MAC address owns the target’s IP address. This is temporary, but attacker needs to periodically spoof ARP responses 
- This leads to sniffing, MITM, session hijacking, DoS


Defenses
- Set up a static ARP entry in the ARP table for hosts that regularly communicate
- E.g., “publish” MAC address of router/default gateway and trusted hosts                `arp -s 192.168.1.30 01-23-45-67-89-ab`
Detection
- `XArp` or other software implement checking e.g., `arp-validator`
- The idea is to send TCP SYN packet to check if the advertised ARP has the right MAC and IP mapping – legit ARP packet if a TCP ACK or RST is received
Smart switches
- Remember MACs
- Assign hosts to specific ports

# References
- [[ARP]]
- [[Denial of Service Attacks and DDoS Attacks]]