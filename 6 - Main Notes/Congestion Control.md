
2025-11-19

Tags: [[Networking]]
# Congestion Control

## Causes of Congestion
---
**Case 1:** In the simplest scenario with a single router (infinite buffers, capacity of R, two flows, no re-transmissions needed). As the arrival rate $\lambda_{in}$ approaches R/2 there will be exponentially increasing delays for all further packets.

**Case 2:** In a case with one router and finite buffers, with the sender re-transmitting lost/timed out packets. Ideally the sender would only re-transmit packets when the router's buffers are available, but this requires perfect knowledge. In practice with partial knowledge the sender only knows when packets are dropped, and packets can be dropped when the router's buffers are too full. **un-needed duplicates** is when packets can be lost or dropped but the sender times out prematurely, resulting in wasted transmissions

**Case 3:** This case is similar to case 2 but if the number of packets becomes high enough then without control a gridlock can occur.
![[Pasted image 20251119231843.png]]
## Fixing Congestion
---
**End to End Congestion Control** To fix these issues we implement congestion control where no feedback is needed and congestion is **inferred** from packet losses and delays. This is the approach taken by TCP.

**Network Assisted Congestion Control**
routers send direct feedback to the sending/receiving hosts with flows passing through congested router. This approach might indicate congestion level or explicitly set the sending rate

# References
[[TCP]]