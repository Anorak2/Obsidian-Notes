
2025-12-05

Tags: [[Networking]] 
# Wireless Networks
Wireless networks allow for devices to connect to a network non-physically, and they are composed to a base station and a wireless link. Base stations are typically connected to the wired network and they act as a relay, responsible for sending packets to the wired network. The wireless links are use to connect the mobile devices to the base stations using multiple access protocols to coordinate access.

![[Pasted image 20251205180958.png]]
![[Pasted image 20251205181006.png]]

## Characteristics
---
- decreased signal strength: radio signal attenuates as it propagates through matter (path loss) 
-  interference from other sources: wireless network frequencies (e.g., 2.4 GHz) shared by many devices (e.g., WiFi, cellular, etc. )
- multipath propagation: radio signal reflects off objects ground, arriving at destination at slightly different times

**Attenuation:** Due to things such as the square cube law, power is lost as it spreads out to a larger and larger area 

**Multipath:**  radio signal reflects off objects ground, built environment, meaning that signals will arrive at the destination at slightly different times.
![[Pasted image 20251205181242.png]]

**Signal to Noise Ratio (SNR) vs Bit Error Rate (BER):**
the larger the SNR the easier it is extract data from the wireless link. This introduces a trade-off where increasing power decreases the BER. This means we will want to choose a physical layer that matches with the BER requirement and therefore giving the highest throughput, this can also dynamically adapt.

**Hidden Termination Problem**
![[Pasted image 20251205181711.png]]
- B, A hear each other
- B, C hear each other
- A, C can not hear each other which means that A and C unaware of their interference at B

**Signal Attenuation Problem**
![[Pasted image 20251205181756.png]]
- B, A hear each other
- B, C hear each other
- A, C can not hear each other interfering at B
# References
[[Multiple Access Protocols]]
