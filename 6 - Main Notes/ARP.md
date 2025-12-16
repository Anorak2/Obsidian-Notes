
2025-11-20

Tags: [[3b - Classes/Networking]] [[Networking]]
# ARP
 ARP, or the address resolution protocol, is used for finding the conversion between IP address and MAC address on a LAN. ARP operates at level 3 but often interacts with link layer due to it's nature. Since we don't want to send an ARP request for every packet we also have an **ARP cache** that stores mac addresses for future use, with a timeout to add resiliency. Often the time to live of an ARP cache is 20 minutes.

#### Types:
1. **Proxy ARP** is when a proxy devices responds on behalf of another device, for example a router may do this
2. **Gratuitous ARP** is when a host sends an ARP request for it's own IP address, often used to detect duplicate IP addresses
3. **Reverse ARP** (`RARP`) is used by a device to discover it's own IP address when it only knows it's MAC address
4. **Inverse ARP** (`InARP`) is used to discover the IP address from a known MAC address, the example given was that it's common in technologies like Frame Relay's and ATM networks

#### Working
- Sender checks if there is a mac-IP conversion already in its cache
- if not cached, an **ARP request** is broadcasted to all devices on the local network
- all devices receive that request and check if that IP equals it's own
- The device assigned with a matching IP address then sends a unicast **ARP reply** containing its mac address
- the sender then updates it's ARP cache for future use

#### Message Format
![[Pasted image 20251207152955.png]]


# References
[[MAC Addresses]]
[[IP v4 Protocol]]
[[Network IP assignment]]
[[Routers]]
