
2025-11-20

Tags: [[Networking]]
# DHCP
The Dynamic Host Control Protocol is how we are able to assign IP addresses to a host. The goal is to have a host dynamically get assigned an IP when it joins the network where it can later renew its lease for an in-use address and allows for reuse of addresses by recycling IP's no longer in use.

**DHCP assignment:**  
- host broadcasts DHCP discover message \[optional\]  
- DHCP server responds with DHCP offer message \[optional]  
- host requests IP address: DHCP request message  
- DHCP server sends address: DHCP ACK message

- DHCP Negative Acknowledgement when the server receives a request that is invalid
- DHCP Decline when a client finds the offered parameters are different or invalid
- DHCP Release when a client ends its lease early and voluntarily
- DHCP Inform is when a client has manually obtained an IP address
![[Pasted image 20251120010656.png]]
**Other things that DHCP can return include:**
- address of first-hop router for client  
- name and IP address of local DNS sever  
- network mask (indicating network versus host portion of address)




# References
[[IP v4 Protocol]]
[[IP v6 Protocol]]
