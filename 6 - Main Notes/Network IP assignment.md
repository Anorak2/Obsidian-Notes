
2025-11-20

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# Network IP assignment
While local IP assignment can be done through DHCP it gets more complicated when the network needs to get it's IP address. The network gets allocated a portion of the ISP's total addressing space and it can then go out and tell the internet to send anything beginning with a certain prefix to that ISP, ex: anything beginning with 199.31.0.0/20 or 200.23..18.0 may go to ISP-r-us where it can then serve that traffic to a lower level organization with an IP address such a 200.23.18.0/23

**How are IP's assigned to ISP's?**
ICANN, or the Internet Corporation for Assigned Names and Numbers allocates IP addresses through regional registries who may then allocate to local registries. ICANN also manages the DNS root zone including the delegations of Top Level Domains such as .com, .edu, etc.
# References
[[IP v4 Protocol]]

[[DHCP]]

