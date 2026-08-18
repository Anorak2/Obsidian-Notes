
2026-05-11

Tags: [[Web]] [[Networking]] [[Network Security]]
# General Anonymous Communication
Anonymity is The ability to hide the identity of the parties involved in digital communications, not only from third-parties but also from each other. The problem is that internet routing is fully incompatible with anonymity since you need to expose an IP etc.

First who wants anonymity? The obvious answer is the bad guys like the spammers, attackers to launch network attacks, terrorism, illegal sharing of copyrighted items, etc. However it isn't just that simple since there are other reasons like law enforcement tools, whistleblowing, unmonitored access to sensitive information (health, medical, etc.), privacy-savvy protection, circumvent censorship, preservation of democracy (anonymous elections, anonymous juries, anonymous donations, etc.)

Anonymity requires unobservability, this means the item of interest is indistinguishable from all other items. Can be done by forwarding anonymous traffic via a network overlay, or through overlay nodes that act as intermediaries between sender and receiver.

Anonymity requires unlinkability. This means that we cannot link two packets entering or existing the intermediaries. Use cryptography to prevent eavesdropper.
## The Dining Cryptographers problem
https://www.cs.cornell.edu/people/egs/herbivore/dcnets.html

The setup is:
- 3 (or N) cryptographers are sitting down to dinner.
- Their waiter tells them the bill is to be paid anonymously, either by one of the cryptographers or by the NSA.
- The three cryptographers respect each other's right to make an anonymous payment, but they wonder if the NSA is paying.
- They want to find a way to check if one of them paid for the dinner.

 DC-Net:
- Phase 1: each diner exchanges a secret with his neighbors, for example, flip a coin with each neighbor
- Phase 2: each diner XOR the two secret with two neighbors. If the cryptographer didn’t pay for the dinner, they report the XOR; otherwise, they report the inverse of XOR
- Then XOR each announced answer `A_announced XOR B_announced XOR C_announced`, if it was 1 then a cryptographer paid otherwise the NSA paid. This works because formally there exists a coin value such that it could explain a particular person's behavior 

The beauty of this is that it achieves perfect anonymity with no trusted third party. The limitations are:
- Collisions (multiple users send at the same time)
- Malicious insider (a malicious use can break the protocol, the last diner can choose the result)
- Require pairwise keys, so not scalable

## Formally
**Strength of Anonymity**
- Exposed: The adversary can identify the sender with certainty
- Possible Innocence: A user is possibly innocent with a nontrivial probability (there exists another party that is more likely to be the communicating party)
- Probable Innocence: The probability that a party is the sender/receiver is significantly less than ½
- Beyond Suspicion: All participants have equal probability of being sender/receiver

**Threat Model:**
The threat model is often modeled as a Byzantine attacker with limited view of the network
- He is more than a passive attacker
- He can deviate arbitrarily from the protocol
- He can have tight control over a network
- He cannot observe the entire Internet

**Measuring Anonymity**
$\Psi$ = anonymity set
$U$ = the probability distribution over $\Psi$
$p_u$ = the probability that u is the sender/receiver according to U
![[Pasted image 20260511211710.png]]


$p_u^0$ is the priori probability that u is the sender/receiver according to $U^0$
$p_u^1$ is the posteriori probability that u is the sender/receiver according to $U^1$
Degree of anonymity measures the effectiveness of the anonymity technique:
$$D=\frac{S^1}{S^0}=\frac{-\sum p_u^1 \times \log p_u^1}{-\sum p_u^0 \times \log p_u^0}$$

# References
- [eff anonymity](https://www.eff.org/issues/anonymity)
- [[Virtual Private Networks (VPN)]]
- [[Decentralized Anonymity - Onion Routing + TOR]]
- 