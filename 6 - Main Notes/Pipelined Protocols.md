
2025-11-19

Tags: [[Networking]]
# Pipelined Protocols
## Stop and Wait
--- 
In this protocol the sender literally waits for the receiver to acknowledge each packet individually before sending the next packet

## Go Back N
---
![[Pasted image 20251119224140.png]]
In this version the sender can have up to N packets in the pipeline and the receiver only has to send a cumulative ACK, and doesn't send an ACK for any packet received after a gap. The sender has a timer for the oldest unacked packet and if the timer expires resend all N packets.

## Selective Repeat
---
![[Pasted image 20251119224200.png]]
The sender can have up to N unacked packets in the pipeline and the receiver sends an individual ACK for each packet. The sender maintains an individual timer for each packet and when the timer expires it only re-transmits that packet.

The **problem** with selective repeat is that if the receiver sends an ACK for a packet it has no way of knowing if that ACK reached it's target, so the sender may repeatedly send packets the receiver doesn't expect. The **fix** is that the size of the sequence numbers should be at least two times the size of the window size.
# References

