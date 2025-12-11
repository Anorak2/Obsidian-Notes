
2025-12-05

Tags: [[Networking]] [[EECS 563 - Intro to Comm Networks]] 
# Multiple Access Protocols
A multiple access protocol is when there is a single shared channel and when two or more nodes may simultaneously transmit. A multiple access protocol is a distributed protocol determining how nodes share a channel. This is tricky because **all** communication must share the channel itself.

**Ideal Multiple Access Protocol:**
1. when one node wants to transmit, it can send at rate R.
2. when M nodes want to transmit, each can send at average rate R/M
3. fully decentralized:
	- no special node to coordinate transmissions
	- no synchronization of clocks, slots
4. simple

**There are three broad classes:**
- Channel Partitioning, where the channel is divided into several slots
- Random access, where the channel isn't divided and collisions are allowed
- "taking turns" where nodes take turns and nodes with more to say can take longer
## TDMA
---
Time division multiple access allows access to the channel in rounds, each node is given a fixed slot each round and unused slots go idle.
![[Pasted image 20251205222307.png]]
## FDMA
---
channel spectrum divided into frequency bands  
- each station assigned fixed frequency band 
- unused transmission time in frequency bands go idle  
- example: 6-station LAN, 1,3,4 have packet to send, frequency bands 2,5,6 idle
![[Pasted image 20251205222346.png]]
## ALOHA
---
**Assumptions:**
- all frames same size  
- time divided into equal size slots (time to transmit 1 frame)  
- nodes start to transmit only at the beginning of a slot  
- nodes are synchronized  
- if 2 or more nodes transmit in slot, all nodes detect collision

**operation:**  
- when node obtains fresh frame, transmits in next slot  
- if no collision: node can send new frame in next slot  
- if collision: node retransmits frame in each subsequent slot with probability p until success

**Pros:**
- single active node can continuously transmit at full rate of channel
- highly decentralized: only slots in nodes need to be in sync
- simple

**cons:**
- collisions, wasting slots
- idle slots
- nodes may be able to detect collision in less than time to transmit packet
- clock synchronization

At best slotted ALOHA will have the channel used for useful transmission only **37%** of the time, in "pure" ALOHA with no time slots the efficiency drops to **18%**.
## CSMA
---
Carrier Sense Multiple Access

**simple CSMA: listen before transmit:**  
- if channel sensed idle: transmit entire frame  
- if channel sensed busy: defer transmission  
- human analogy: don’t interrupt others

**CSMA/CD: CSMA with collision detection**  
- collisions detected within short time  
- colliding transmissions aborted, reducing channel wastage  
- collision detection easy in wired, difficult with wireless  
- human analogy: the polite conversationalist

**Ethernet Algorithm**
1. NIC receives datagram from network layer, creates frame  
2. If NIC senses channel:  
	- if idle: start frame transmission.  
	- if busy: wait until channel idle, then transmit  
3. If NIC transmits entire frame without collision, NIC is done with frame !  
4. If NIC detects another transmission while sending: abort, send jam signal  
5. After aborting, NIC enters binary (exponential) backoff:  
	- after mth collision, NIC chooses K at random from {0,1,2, ..., 2m-1}. NIC waits K·512 bit times, returns to Step 2  
	- more collisions: longer backoff interval
## CDMA
---
In CDMA a unique “code” assigned to each user i.e. code set partitioning. All users share same frequency, but each user has own “chipping” sequence (i.e., code) to encode data.

This allows multiple users to “coexist” and transmit simultaneously with minimal interference (if codes are “orthogonal”).
- encoding: inner product: (original data) X (chipping sequence)
- decoding: summed inner-product: (encoded data) X (chipping sequence)
![[Pasted image 20251205224728.png]]
# 802.11
---
![[Pasted image 20251205224829.png]]
 wireless host communicates with base station
- base station = access point (AP)
- Basic Service Set (BSS) (aka “cell”) in infrastructure mode contains:
	- wireless hosts
	- access point (AP): base station
	- ad hoc mode: hosts only
The spectrum is divided into channels at different frequencies to prevent overlapping in the immediate area  
	- AP admin chooses frequency for AP  
	- interference possible: channel can be same as that chosen by neighboring AP!
![[Pasted image 20251205225032.png]]

arriving host: must associate with an AP  
- scans channels, listening for beacon frames containing AP’s name (Service Set ID -- SSID) and MAC address  
- selects AP to associate with  
- then may perform authentication  
- then typically run DHCP to get IP address in AP’s subnet

- avoid collisions: 2 + nodes transmitting at same time  
- 802.11: CSMA - sense before transmitting  
	- don’t collide with detected ongoing transmission by another node  
- 802.11: no collision detection!  
	- difficult to sense collisions: high transmitting signal, weak received signal due to fading  
	- can’t sense all collisions in any case: hidden terminal, fading  
	- goal: avoid collisions: CSMA/Collision Avoidance

![[Pasted image 20251205225357.png]]
![[Pasted image 20251205230312.png]]

# References
