# 1
---
a.
1. Host E sends Ethernet frame to Router 2 
2. Router 2 forwards to Router 1
3. Router 1 forwards to Host B
4. Host B receives packet.

b.
1. Host E performs ARP request for Router 2.
2. Router 2 replies with MAC 77-...
3. Host E sends Ethernet frame to Router 2.
4. Remaining forwarding steps unchanged from part (a).
# 2
---
i. 
the switch learns

MAC          Port
A              A-port


ii.
the switch learns about d 
MAC          Port
A              A-port
D              D-port

iii.
the switch learns about c
MAC          Port
A              A-port
D              D-port
C              C-port

iiii.
the switch already knows about A so it stays the same
MAC          Port
A              A-port
D              D-port
C              C-port


# 3
---
first the computer will request an IP from dhcp, the dhcp server will offer an IP, and the computer will accept that IP. Next the computer will send a dns request embedded in UDP embedded in IP which gets sent out to a dns server, if it isn't known then that server will ask the big 13 and then a top level domain which will then return the authoritative name server which will tell the proper IP address. from there if you want to download a webpage in HTTP-3 then it will send that in QUIC form, which uses udp, which is wrapped in IP which is sent to your computer so that you can view it.

# 4 
---

# NAT lab 
---
a.
192.168.10.11 port 53924 to 138.76.29.8 port 80
![[Pasted image 20251204233949.png]]
b.
time 0.030672101
c.
src ip 138.76.29.8 to dest 192.168.10.11
src port 80, dest port 53924
d.
this comes from time 0.027356291
![[Pasted image 20251204233508.png]]
e.
the source port is 80 and the dest port is 53924. The source IP and destination IP changed but the ports stayed the same
![[Pasted image 20251204233704.png]]
f.   0.030625966

g.
source IP is 138.76.29.8 to the dest 10.0.1.254, source port 80 to port 53924
![[Pasted image 20251204234501.png]]
h.
the data is forwarded from 138.76.29.8 to 10.0.1.254 which then applies NAT and sends the traffic to 192.168.10.11
# ARP lab
---
a.
00:1e:c1:7e:d9:01

b.
It contains a value but it is fully blank
Target MAC address: 00:00:00_00:00:00 (00:00:00:00:00:00)

c.
it does contain the IP address, 128.119.247.1
![[Pasted image 20251204234842.png]]
d.
Target IP address: cicspc-us-103.cs.umass.edu (128.119.247.77)

e.
Target IP address: 128.119.247.66 (128.119.247.66)
this came from a different ARP request