
2025-11-20

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# Network Address Translation (NAT)
NAT is an interesting technique where all devices in local network share just one IPv4 address as far as outside world is concerned. All of the datagrams leaving the network will have the same source IP address but different source port numbers, and all of the addressing in the local network will be done with a reserved IP address like 10/8, 172.16/12, 192.168/16 that can **only** be used locally.

**Advantages:**
- just one IP address needed from ISP for all devices  
- can change addresses of host in local network without notifying outside world  
- can change ISP without changing addresses of devices in local network  
- security: devices inside local net not directly addressable, visible by outside world

#### Implementation:
NAT router must (transparently):  
- outgoing datagrams: replace (source IP address, port #) of every outgoing datagram to (NAT IP address, new port #)  
- remote clients/servers will respond using (NAT IP address, new port #) as destination address  
- remember (in NAT translation table) every (source IP address, port #) to (NAT IP address, new port #) translation pair  
- incoming datagrams: replace (NAT IP address, new port #) in destination fields of every incoming datagram with corresponding (source IP address, port #) stored in NAT table
#### Controversy
Port numbers are used to address hosts in NAT but really ports should only be used to address processes, routers also "should" only process up to level 3, and the shortage of IPv4 address "should" be solved by IPv6. However despite all of that NAT is used extensively in home networks and institutional networks.
# References

