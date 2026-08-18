
2026-05-11

Tags: [[Web]] [[Networking]] [[Networking]]
# Decentralized Anonymity - Onion Routing
Onion Routing is a design proposed by Reiter and Rubin in 1998. It's an overlay network called “crowd” with a group of “jondos” or john does. The idea is to hide the sender among jondos – anyone could send the message to the receiver.

##  Basic Crowds
Two Steps:
1. Sender relays message to a random jondo;
2. With probability $p_f$ , a jondo forwards message to another jondo; with $(1 - p_f )$, it forwards the message to the receiver

Anonymity (with a set of n jondos):
- Observe at the sender: receiver anonymity is protected, sender anonymity is exposed
- Observe at the receiver (or in the network): sender anonymity is protected
- If any message is intercepted: receiver is trivially exposed
If c jondos are malicious: the sender is probable innocence if:
$$n \gt \frac{p_f}{p_f-0.5}(c+1)$$
## Mix Networks
Originally designed for anonymous email `[David Chaum, 1981]` that can be generalized for TCP traffic. It influences several later designs such as traffic mixing,  dummy traffic, and onion routing. 

Steps:
1. Mix collects messages for t seconds
2. Messages are randomly shuffled and sent in a different order

This hinders timing attacks since messages may be artificially delayed, thus the "temporal correlation" is warped. However the limitations are that it requires lots of traffic and adds additional latency to network flows.

## Dummy / Cover Traffic
Simple idea: Send useless traffic to help obfuscate the real traffic
![[Pasted image 20260511213613.png]]

## Onion Routing
Onion entry funnel source-routes messages through series of randomly chosen onion routers. Onion exit funnel can then relays messages out of the network to the destination. Then reply traffic can simple traverse the reverse path. As a result, it establishes bidirectional persistent multi-hop path between sender and recipient.

**Setup**
- Source routing: the onion entry funnel sends onions to onion routers selected for the source-routed path
- Layered encryption: it informs each router only about its next hop (hiding the receiver address and port)
- Each onion router knows its previous hop from the IP header
- Each onion router mixes traffic from potentially multiple sources
- Key seed material is hashed to generate forward and reverse keys

**Data Phase**
- Onion entry funnel uses layered encryption to encrypt data
- Use keys in the reverse order. This means the onion router decrypts the outermost layer and forwards it to next stop
- In the reverse route each hop adds a layer of encryption using backwards keys, and the onion entry funnel decrypts the reply and relays it to the proxy.

![[Pasted image 20260511213916.png]]

## TOR: The second generation Onion Router
TOR is a mix network with improvements (8K+ routers and 2M+ users), and it can provide:
- Perfect forward secrecy
- Introduces guards to improve source anonymity
- Introduces sessions for long-term communications
- Takes bandwidth into account when selecting relays, removing the high latency delays
- TOR also introduces hidden services that are servers that are only accessible via the Tor overlay

**Perfect Forward Secrecy**
In traditional mix networks, all traffic is encrypted using public/private keypairs
What happens if a private key is stolen?
- All future traffic can be observed and decrypted
- If past traffic has been logged, it can also be decrypted

Tor implements Perfect Forward Secrecy (PFC)
- The client negotiates a new public key pair with each relay
- Original keypairs are only used for signatures, i.e. to verify the authenticity of messages
- An attacker who compromises a private key can still eavesdrop on future traffic
- But past traffic is encrypted with ephemeral keypairs that are not stored

**How are relays located?**
Tor Consensus File is hosted by trusted directory servers and lists all known relays: IP address, uptime, measured bandwidth, … Note that not all relays are created equal, specifically entry/guard and exit relays are special. Tor also does not select relays randomly, it gives a chance of selection is proportional to bandwidth.

**Guard Relays**
Guard relays help prevent attackers from becoming the first relay
- Tor selects 3 guard relays and uses them for 3 months
- After 3 months, 3 new guards are selected
Only relays that have long and consistent uptimes, have high bandwidth, and are manually vetted may become guards. if an evil guard is chosen then there is a M/N chance of full compromise

**Onion Services**
- Tor can also provide anonymity to websites and servers, known as Onion services or hidden services
- This allows internet users to connect to the website without disclosing it domain name or IP address
- Sites have a .onion address, only accessible to users through Tor
- Sometimes this is called the Dark Web since it can't be accessed through non-tor networking
![[Pasted image 20260511220340.png]]


**Problems:**
Anonymity systems weaken protection against
- Eavesdropping
- On-path attacks
- Routing attacks

# References
- [[General Anonymous Communication]]