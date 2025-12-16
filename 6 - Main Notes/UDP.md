
2025-11-19

Tags: [[3b - Classes/Networking]] [[Networking]]
# UDP
UDP, or the User Datagram Protocol, exists to provide unreliable and unordered delivery of data unlike it's brother [[TCP]]. It is essentially a "no-frills" extension of the [[IP v4 Protocol]]. UDP is described in `RFC 768`. UDP provides nothing extra, as you can see in the picture below it literally only provides the src, dest, checksum, and length of the packet and no more. It exists since there is no RTT delay with establishing a connection, it's incredibly simple,  it has a very small (8 byte) header size, and no congestion control so it can just blast data at a target. **UDP is often used for** streaming apps, DNS, SNMP (simple network management protocol), and HTTP/3. For most of these applications we care more about speed and efficiency than maximizing reliability, and if reliability or congestion control is needed it can be added at the application layer.

![[Pasted image 20251119222205.png]]

**Demultiplexing/ports:** Something very significant about UDP is that when the packets arrive at the source IP address, if they have the same destination port # then even with different source IP's they will be directed to the same socket. We typically get the destination port number through either well known port numbers or through some other protocol first.

# References
[[TCP]]

[[Ports]]
