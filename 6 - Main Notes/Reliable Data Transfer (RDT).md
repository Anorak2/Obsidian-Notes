
2025-11-19

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# Reliable Data Transfer (RDT)
The principles of reliable data transfer are something of an abstract framework for how to create reliability in data transport without being a fully formed practical implementation.

**Goals:**
1. Data Integrity
	- No packet loss
	- No packet duplicated
	- In-order delivery
2. Flow Control
	- avoid overflowing the receivers buffer

**Remarks**
Complexity of reliable data transfer protocol will depend (strongly) on characteristics of unreliable channel (loss, corrupt, reorder data?)

Sender, receiver do not know the “state” of each other, e.g., was a message   received? Unless it was communicated via a message

#### RDT 1.0
The underlying channel was perfectly reliable with no bit errors and no loss of packets.

#### RDT 2.0
This version seeks to answer two problems with reliability: How do we detect errors at the receiver and how do we recover from errors?
- Acknowledgements; receiver will explicitly tell the sender that the packet was ok
- Negative Ack's: receiver explicitly tells the sender that the packet had errors.

**Duplicates?** This was one problem, so RDT 2.0 added sequence numbers so that a duplicate packet could be discarded.

**ACK/NAK Corrupted?** This is the fatal flaw with RDT 2
# References

