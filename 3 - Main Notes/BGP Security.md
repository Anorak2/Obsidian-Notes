
2026-02-10

Tags: [[Networking]] [[Network Security]]
# BGP Security
BGP is routing protocol in between AS but not everyone agrees on the "best" paths. ISP's want to retain control over routing, and will sometimes make deals to route traffic or will try to avoid others for security or other reasons. We have gotten closer to a global solution but often the problems with BGP aren't technical and are instead related to costs, backwards compatibility, and incremental deployment.

### BGP Policies
Valley-free export policy
- Customer → Provider: you pay the provider (traffic goes “up”)
- Peer <-> Peer: settlement-free exchange (traffic crosses “sideways”)
- Provider → Customer: provider carries you (traffic goes “down”)

ASes has considerable flexibility in how they select their routes
- Decisions are typically independent of the performance of the route
- Instead, they are based on route length (# of ASes on route) and the price of forwarding traffic to that announcing neighbor. Charges may be based on traffic volume: My customer sends me a lot of data → good, I have to send data to my provider → bad
![[Pasted image 20260210095352.png]]

### BGP Announcements
Routes in BGP are announced at the prefix level, ie I may advertise my AS 22394 owns 66.174.161.0/24. Asides from origin announcements (ownership), BGP also can send route advertisements and route withdrawals.
![[Pasted image 20260210095919.png]]
### Attacks
**Prefix Hijack:**
An attacker claims to own a known prefix that belongs to some other. Hijacks and sub-prefix hijacks can happen because BGP lacks basic authentication of AS's and IP addresses making it easy for an attacker to forge a message. This can lead to a black hole when addresses are messed with that is out of our site.

**Sub-prefix Hijack:**
Attacker originates a sub-prefix of the victim’s IP prefix which can be much more dangerous than prefix hijacking. Attacker can hijack all traffic to the victim – longer prefix first. Part of why this is a problem is that it's a black hole to the victim, they will have a difficult time understanding what is going wrong.

**Path Forgery:**
Since BGP is a path-vector protocol the length of a path is very significant when routing. If an AS_PATH attribute is forged then an attacker has control over the flow of traffic, though as discussed this can happen on accident as well.

**Prefix Destabilization**
Cause BGP dampening at the victim peer, so routes that flap will be penalized by being suppressed

**Link Cutting**
If the attacker knows the network topology, bringing down certain links (through DoS
attacks or a backhoe) can force traffic into the pattern they desire. Done by taking over the control of the router, or physically destroying the router.
### BGP Issues
This is the biggest issue with BGP and the leading cause of instability in the internet, 200-1200 prefixes are misconfigured per day. Causes include carelessness, poor configuration tools, bad network requirements... as well as slow detection.
**Route Leaks:**
This is when you announce a legitimate route to "too many" neighbors. For example a smaller AS might broadcast it's route to some place to google leading to another AS to route all of it's google traffic through our small AS leading to an outage.

**BGP Misconfiguration**
 ![[Pasted image 20260210100555.png]]
Origin Misconfiguration 
- Announce an address that is part of another's address space (prefix hijacking
- accidentally advertise fewer IP's than intended  (a.b.0.0/16 to a.b.0.0/24)
- related origin where same prefixes have different paths
- foreign relation is when we advertise a route that has no relation to our original route
![[Pasted image 20260210100652.png]]


### Defenses
A number of fancy protocols were proposed but were never deployed or fully deployed. In reality most deployed techniques for securing BGP have been at the local level. The main techniques are prefix-filtering, cryptography based origin validation (RPKI), and cryptography based path validation (BGPsec). 

**Filtering:**
Filtering drops BGP messages as they are passed between AS's, typically for advertisements. ISP AS's will aggressively filter to serve as the main security mechanism. Filtering can be done by IP prefix, by the path, or by policy (based on the fields in the BGP message).

Rule of Thumb: AS 𝑎 will typically announce a route to a neighbor AS 𝑛 only if
- 𝑛 is a customer of 𝑎
- The route is for a prefix originated by 𝑎
- The route is through a customer of 𝑎

So an AS will keep a small set of prefixes announced by its customer AS's and discard a BGP announcement when it doesn't match the prefixes on the list. This approach is simple and effective but it works only on customer links, it also has unbalanced incentives since the one filtering isn't usually the victim.

**RPKI**
RPKI uses cryptography for origin validation and it provides a trusted mapping from allocated IP prefixes to AS's authorized to originate them in BGP. This protocol has reached 90% adoption among IP addresses so it is very significant. RPKI works by establishing a hierarchy rooted at regional local internet registries (RIRs). This allows the holder of the prefix certificate to sign a Route Origin Authentication (ROA) which authorizes an AS to originate a prefix. 

The benefits are that it gives protection against hijacks, it's easy, offline cryptography where updates are verified once per day, no need to change BGP message format, and the incentives are effective since if you don't contribute you will be ignored. The challenge is that RPKI is not perfect and there are issues with RPKI take-downs, misconfigurations, and abuses. It also doesn't work for route leaks or path shortening attacks.

**BGPsec:**
BGPsec provides path validation by requiring Autonomous Systems to sign each of its BGP messages. An AS will receive the prefix and AS level path, the AS number of the AS receiving the message, and all of the signed messages from previous AS's.

The benefit is that path shortening attacks can't work in this system but it comes with challenges. This system leads to computation overhead at routers and there is the problem of being a first adopter due to limited support.

# References
- [[Border Gateway Protocol (BGP)]]

