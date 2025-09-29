
2025-04-01

Tags: [[Networking]] [[Security]] [[Applied Cybersecurity]]
# Denial of Service Attacks and DDoS Attack
A denial of service attack is when an attacker aims to disrupt a targets business by preventing legitimate users from being able to access a business. When we have multiple or attackers or bots working to take down a website at the same time that is a DDoS attack. Examples of how we could deny service include flooding a network (the flashiest), attempts to disrupt connections between two machines, attempts to prevent a singular person from connecting, or attempts to prevent a service from connecting. Classes of DoS attacks include: 
- Vulnerability DoS Attacks (Ping of Death, Nuke)
- Reflector DoS Attacks (smurf attacks, amplification attacks)
- Flooding DoS Attacks (e.g. SYN flood, ICMP flood, UDP flood)
- Slowloris Type DoS Attacks

## Specific Attacks
#### ICMP Flood (smurf attack)
In a Smurf attack an attacker sends ICMP echo request messages to a broadcast address at an intermediate site (source address in each request packet is spoofed so that replies are sent to a victim machine). From the server's POV it looks like, say, google’s DNS servers are DDoS'ing you. This is solved by configuring machines to not respond to ICMP echo requests sent to a broadcast address.

#### UDP Flood
An attacker can instead just send a huge number of UDP packets to the target host, and as a result the target host becomes overloaded and can no longer reply to requests from legitimate users. There really aren't that many solutions to fix this, we can do packet rate limiting. We can also try filters but since most UDP packet filters are based on simple patterns.

#### Syn Flood
An attacker sends a flood of TCP/SYN packets, often with a forged sender address. The victim machine will handle each of these packets like a connection request and it will wait for a packet in response from the sender address. Because the address was spoofed the response never comes, so the request will sit until it times out. These half open connections saturate the number of connections the server is able to make, resulting in a victim unable respond to legitimate requests. Solved by using SYN cookies.

#### Amplification Attacks
**DNS**: Similar to a smurf attack, attackers target open recursive DNS servers using a spoofed source IP, and there's no one size fits all solution to fixing this either.

**Memcached amplification:** where publicly routable Memcached servers targeted and sent packets with spoofed source IP It’s possible to get an amplification factor of 51,000 which means that every byte sent by the attacker 51 KB were sent to the target. Solution: disable UDP on Memcached servers and to firewall servers from the public facing internet.

#### Ping of Death and Nuke attacks
In a ping of death attack the attacker constructs an ICMP echo request message which when encoded the resulting size is 65,538 bytes which overflows the IP protocol limit of 65,536 bytes. Easily fixed in software. 

**Nuke attacks** this is where a packet of data is sent that the OS can't handle, leading to a crash.
#### Slowloris
https://www.cloudflare.com/learning/ddos/ddos-attack-tools/slowloris/
This is a type of attack where we try to keep as many connections open on the target server as possible, and keep those connections open as long as possible. (https://github.com/gkbrk/slowloris) this is an example of a Slowloris attack.

**DoS/DDoS Tools**

```LOIC (Low Orbit Ion Cannon)```
LOIC is an open source network stress testing application written in C#. It offers three kinds of attacks using either UDP, TCP, or HTTP. They all work similarly though where it opens several connections to the host and continually sends a predefined string (payload). In the TCP and UDP attacks this is just sent in plaintext, and in the HTTP version its just the body of a GET request. It uses the same payload for every packet and the source IP address is not spoofed. 

```Trin00```
```Tribe Flood Network```
```Stacheldraht```
# References
[[HTTP]]
