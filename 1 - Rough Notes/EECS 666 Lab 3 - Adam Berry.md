
```javascript
iptables -F
iptables -P OUTPUT ACCEPT
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
```
# 2
**2.1**
![[screenshot-2026-04-27-22 00 49.png]]
I'm able to ping the router but telnet is fully unable to see the host

iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
- Allows incoming ICMP echo requests
iptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT
- allows outgoing ICMP echo remplies
iptables -P OUTPUT DROP
- drop all other packets trying to leave the network
iptables -P INPUT DROP
- drop all other packets trying to enter the network

**2.2**

iptables -A FORWARD -p icmp --icmp-type echo-reply -j ACCEPT
iptables -A FORWARD -p icmp --icmp-type echo-request -j DROP
iptables -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
![[screenshot-2026-04-27-22 12 16.png]]

iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT
iptables -P OUTPUT DROP
iptables -P INPUT DROP

// allow internal to ping external
iptables -A FORWARD -p icmp --icmp-type echo-request -i eth1 -o eth0 -j ACCEPT
// Allow echo replies from outside
iptables -A FORWARD -p icmp --icmp-type echo-reply   -i eth0 -o eth1 -j ACCEPT

// outside cannot ping internal
iptables -A FORWARD -p icmp --icmp-type echo-request -i eth0 -o eth1 -j DROP
//  drop outbound pings to internal hosts
iptables -A FORWARD -p icmp --icmp-type echo-request -i eth0 -o eth1 -j DROP
iptables -P FORWARD DROP

![[screenshot-2026-04-27-22 23 08.png]]
internal -> External pings are allowed

![[screenshot-2026-04-27-22 23 48.png]]
external -> internal blocked

**2.3**

```bash
# Flush the tables
iptables -F
# Set internal default to accept, others to drop
iptables -P INPUT ACCEPT 
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# Inbound connection attempt (eth0 -> eth1, destined for .60.5 port 23)
iptables -A FORWARD -i eth0 -o eth1 -p tcp -d 192.168.60.5 --dport 23 -j ACCEPT

# Reply packets back out (eth1 -> eth0, sourced from .60.5 port 23)
iptables -A FORWARD -i eth1 -o eth0  -p tcp -s 192.168.60.5 --sport 23 -j ACCEPT

```


![[Screenshot-2026-04-27-22 58 48.png]]
This shows how from the external node we can connect only to 60.5 and not the other two nodes over telnet

![[Pasted image 20260427230029.png]]
from an internal host .6 we can connect to .7 but not 10.9.0.5
# 3 
**3.1**
1.
![[Screenshot-2026-04-27-23 15 28.png]]
![[Screenshot-2026-04-27-23 17 08.png]]
On conntrack the ICMP state is kept for 30 seconds

2.
![[Screenshot-2026-04-27-23 18 59.png]]
![[Screenshot-2026-04-27-23 19 05.png]]The state isn't kept for UDP, which  given what we know makes sense

3.
![[Screenshot-2026-04-27-23 21 03.png]]
TCP connections are remembered for about 43200 seconds, or 12 full hours

**3.2**

```bash
# Flush the tables
iptables -F
# Set internal default to accept, others to drop
iptables -P INPUT ACCEPT 
iptables -P OUTPUT ACCEPT 
iptables -P FORWARD DROP

# Allow all replies to established connections regardless of protocol
iptables -A FORWARD  -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

# outside can reach only 192.168.60.5
iptables -A FORWARD -i eth0 -o eth1 -p tcp -d 192.168.60.5 --dport 23 \
    --syn -m conntrack --ctstate NEW -j ACCEPT

# internal hosts can make connections tou other servers
iptables -A FORWARD -i eth1 -o eth0 -p tcp \
    --syn -m conntrack --ctstate NEW -j ACCEPT

```
![[Screenshot-2026-04-27-23 28 22.png]]
10.9.0.5 can only connect to 192.168.60.5
![[Screenshot-2026-04-27-23 35 17.png]]192.168.60.6 can connect to outgoing and internal connections regardless of the port used

6. Without using the connection tracking mechanism we could stop TCP packets that have the SYN flag set, this way only our server can initiate connections. Honestly having both doesn't even seem detrimental though perhaps its verbose, but the connection tracking is probably more durable since it won't allow any packets through unless a connection was initiated while stopping SYN tcp packets is simpler
# 4
![[Screenshot-2026-04-27-23 46 47.png]]
I'm worried I messed it up but I can ping as many times as I want to seemingly normally

![[Pasted image 20260427234833.png]]
With this command it got noticably slower after the fifth/sixth ping and packets started dropping


**4.2**
```
iptables -t nat -A PREROUTING -p udp --dport 8080 \
    -m statistic --mode random --probability 0.333 \
    -j DNAT --to-destination 192.168.60.5:8080

iptables -t nat -A PREROUTING -p udp --dport 8080 \
    -m statistic --mode random --probability 0.5 \
    -j DNAT --to-destination 192.168.60.6:8080

iptables -t nat -A PREROUTING -p udp --dport 8080 \
    -m statistic --mode random --probability 1.0 \
    -j DNAT --to-destination 192.168.60.7:8080
```
Set the P of the first one to 0.33 since there's still three left, but for the second rule now there's only 2 nodes it can go to so it's a 50/50 to stay uniform, and for the last one since we passed the other two it's a 100% guarantee
