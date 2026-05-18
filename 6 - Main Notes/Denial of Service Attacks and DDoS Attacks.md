
2025-04-01

Tags: [[Networking]] [[Network Security]] [[Software Security]]
# Denial of Service Attacks and DDoS Attack
A denial of service attack is when an attacker aims to disrupt a targets business by preventing legitimate users from being able to access a business. When we have multiple or attackers or bots working to take down a website at the same time that is a DDoS attack. Examples of how we could deny service include flooding a network (the flashiest), attempts to disrupt connections between two machines, attempts to prevent a singular person from connecting, or attempts to prevent a service from connecting.  DoS attacks are interesting because they can be very hard to avoid, and there is no direct benefit other than the victims pain.

Classes of DoS attacks include: 
- Vulnerability DoS Attacks (Ping of Death, Nuke)
- Reflector DoS Attacks (smurf attacks, amplification attacks)
- Flooding DoS Attacks (e.g. SYN flood, ICMP flood, UDP flood)
- Slowloris Type DoS Attacks

# Attack Classes
## Physical Layer
These are perhaps the least creative attacks but they are also one of the easiest to perform and the hardest to defend against. Attack types include physical destruction, obstruction, manipulation, or malfunction of physical assets. Including: Wire cutting, Physical destruction, equipment manipulation, RF jamming, interference.

## Link Layer
- One way to attack the link layer is is to flood ARP messages to poison the cache [[ARP Attacks*]]. 
- Another way is the DHCP exhaustion attack with spoofed mac addresses with the goal of consuming all addresses in the DHCP server's pool.
- There are also attacks against 802.11 such as sending a deauth frame to an AP with the victim's mac address, or alternatively you could send Auth packets with spoofed addresses to exhaust the resources
## Network Layer
#### Ping of Death and Nuke attacks
In a ping of death attack the attacker constructs an ICMP echo request message which when encoded the resulting size is 65,538 bytes which overflows the IP protocol limit of 65,536 bytes. Easily fixed in software. 

**Nuke attacks** this is where a packet of data is sent that the OS can't handle, leading to a crash.
#### ICMP Flood (smurf attack)
In a Smurf attack an attacker sends ICMP echo request messages to a broadcast address at an intermediate site (source address in each request packet is spoofed so that replies are sent to a victim machine). From the server's POV it looks like, say, google’s DNS servers are DDoS'ing you. This is solved by configuring machines to not respond to ICMP echo requests sent to a broadcast address.
## Transport Layer
#### Syn Flood
An attacker sends a flood of TCP/SYN packets, often with a forged sender address. The victim machine will handle each of these packets like a connection request and it will wait for a packet in response from the sender address. Because the address was spoofed the response never comes, so the request will sit until it times out. These half open connections saturate the number of connections the server is able to make, resulting in a victim unable respond to legitimate requests. Solved by using SYN cookies.

#### DNS Amplification Attacks
Similar to a smurf attack, attackers target open recursive DNS servers using a spoofed source IP, and there's no one size fits all solution to fixing this either.

#### NTP Amplification Attacks
The Network Time Protocol allows for internet-connected devices to synchronize their internal clocks, but vulnerable NTP servers supported a `monlist` command that results in a large response. With just 10 machines with a 1 Gbps connection an attacker was able to get a amplification factor of 6 to 400 amplifier machines resulted in 500 Gbps of network traffic.
#### Memcached Amplification Attacks
where publicly routable Memcached servers targeted and sent packets with spoofed source IP It’s possible to get an amplification factor of 51,000 which means that every byte sent by the attacker 51 KB were sent to the target. Solution: disable UDP on Memcached servers and to firewall servers from the public facing internet.

## Application Layer
#### Slowloris
https://www.cloudflare.com/learning/ddos/ddos-attack-tools/slowloris/
This is a type of attack where we try to keep as many connections open on the target server as possible, and keep those connections open as long as possible. (https://github.com/gkbrk/slowloris) this is an example of a Slowloris attack.
#### UDP Flood
An attacker can instead just send a huge number of UDP packets to the target host, and as a result the target host becomes overloaded and can no longer reply to requests from legitimate users. There really aren't that many solutions to fix this, we can do packet rate limiting. We can also try filters but since most UDP packet filters are based on simple patterns.

#### HTTP flooding
Bots saturate the victim server’s network bandwidth with many established connections, notably they complete TCP connection which will bypass SYN flood protection proxy. Bots send short HTTP GET or POST requests to web server requesting for large files or submitting forms which is easy work for client, but hard work for server.

# Defenses
Defending our resources from exhaustion can be a very difficult problem often requiring isolation mechanisms and reliable identification of different users. It also changes dramatically based on the attack type, against a single machine we could install a network filter to drop any packets with certain source IP's.

**problems:**
- the attacks are often simple to perform
- attack machines are easy to obtain
- attack traffic looks like normal traffic
- there's often a lack of cooperation between targets since ISP's are competitive
- There's a lack of enforcement tools and no incentive to deploy defenses since the internet is hard to change.

## Over-provisioning
This defense strategy is to increase the capacity of both the hardware and the network by using sites so big they can simply serve the traffic to the attacker. There are free services such as Google Project Shield (news), Cloudflare Project Galileo (social groups), as well as paid services like CDNs, Cloudflare, and Incapsula.


## DDoS Filtering Techniques
## Filtering

**Ingress filtering**
- ISP only forwards packets with legitimate source IPs
- Prevents IP spoofing
- Problem: requires most ISPs to adopt it
- In practice there is little incentive for ISPs
Note:
- `spoofer.caida.org` reported 16% of IPv4 blocks were spoofable (2019)

**Anomaly filtering**
- Route traffic through filtering boxes
- Detect DDoS traffic based on unusual patterns
  - abnormal traffic spikes
  - strange packet distributions

**Black-hole routing**
- ISP diverts all traffic to the victim into a sinkhole
- Victim site goes offline
- Advantage: avoids collateral damage to other systems
- Often acceptable since many DDoS attacks are short-lived

**Overlay filtering**
- Uses a secure overlay network
- Overlay nodes:
  - authenticate clients
  - filter traffic
  - forward only legitimate requests to the server

**Capability-based filtering**
- Receiver specifies what packets it accepts
- Sender must request permission to send
## Control Attack Effect
Here we slow down the attackers directly rather than improve the server.
- Router/Firewall: packet/frame inspection, rate limiting, session limiting
- Pushback filtering (`Ioannidis` and `Bellovin` in `NDSS’02`)  Lets a router notify upstream routers to iteratively limit traffic rate or block attacking network segments
- Client Puzzle: During an attack everyone must submit a solution to a puzzle with requests. The puzzle is hard to design but it should be a moderately hard problem that most people are can solve easily.
**Circumvent Automation**
- Verify the connection is coming from a human by challenging the requester, this is nice because we do one challenge per request and it works for application layer DDoS
# Practical
**DoS/DDoS Tools**
```LOIC (Low Orbit Ion Cannon)```
LOIC is an open source network stress testing application written in C#. It offers three kinds of attacks using either UDP, TCP, or HTTP. They all work similarly though where it opens several connections to the host and continually sends a predefined string (payload). In the TCP and UDP attacks this is just sent in plaintext, and in the HTTP version its just the body of a GET request. It uses the same payload for every packet and the source IP address is not spoofed. 

```Trin00```
```Tribe Flood Network```
```Stacheldraht```
# References
- [[HTTP]]
- [[UDP]]
- [[DHCP]]
- [[ARP]]
- [[DNS Servers]]
