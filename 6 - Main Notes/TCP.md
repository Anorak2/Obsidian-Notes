
2025-11-19

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# TCP
TCP, or the Transmission Control Protocol, exists to provide reliable in order communication with congestion control, flow control, and congestion setup baked in. TCP is described in `RFC 793`

**Demultiplexing:** While any UDP packet with a given port number will be directed to that port, in TCP the socket is identified by the combination of the: Source IP address, source port number, destination IP address, and the destination port number.

#### Important properties
- Point-to-point: there is one sender and one receiver
- reliable, in order byte stream: this means no boundaries between messages
- full duplex data; there can be bi-directional data flow in the same connection
- cumulative ACK's
- connection oriented: we initialize the sender/receiver state before a data exchange
- flow controlled: the sender will not overwhelm the receiver

#### Segment Structure
![[Pasted image 20251119224814.png]]
Note that this is about 20 bytes worth of headers.

#### Sequence Numbers
If we are trying to send 50,000 bytes over TCP and suppose the MSS is 1,000 byes. In this case the first byte/segment of the data stream is labeled 0, but the second segment gets the sequence number 1,000, the third segment gets 2,000...

#### Round Trip Time (RTT) Timeout
How do we set the RTT timeout? if we set it too low then there will be unnecessary re-transmissions, but too high and we will have slow reactions to losses. To solve this we can take the exponential weighted moving average of the past few transmissions, with the influence of past packets decreasing exponentially quickly.
$$EstimatedRTT = (1-\alpha )*EstimatedRTT+a*SampleRTT$$
with a typical $\alpha$ value of 0.125
$$\text{Timeout Interval}=EstimatedRTT + 4*DevRTT$$
where the `DevRTT` is our "safety margin"
$$DevRTT = (1-\beta)*DevRTT+\beta*|SampleRTT-estimatedRTT|$$
where $\beta$ typically is set to 0.25

#### Fast Retransmit
If a sender receives three additional ACKs for the same data, then resend the unacked segment with the smallest sequence number. We do this since it is very likely a segment was lost so no need to wait for a timeout.

#### Flow Control
What happens if the network layer delivers faster than the application layer removes data from the socket buffers? Nothing good...

To fix this TCP "advertises" the free buffer space in the `rwnd` field of the TCP header. The Receiver buffer is often set to 4096 bits but many operating systems auto adjust the `rcvnbuffer`. The sender then limits the amount of unacked in flight data to the received `rwnd`, guaranteeing the buffer won't overflow.
#### Three Way Handshake and Closing
Client                                           Server
------                                           ------
   |                                                                                  |
   | ----------------- SYN (Synbit =1, Seq = x) --------------------------> |
   |                                                                                  |
   | <--- SYN + ACK (Synbit = 1, Seq = y, AckBit = 1,  Ack = x+1) --------- |
   |                                                                                  |
   | ---------------- ACK (Ackbit = 1, Ack = y+1) ------------------------> |
   |                                                                                  |
   |  Connection Established

**Closing a Connection**
![[Pasted image 20251119230838.png]]
Fin ->        <- Ack       // One who sent fin can no longer send but still receive
Ack ->      <- Fin

// Timed wait period for client to ensure server received ACK
#### TCP Congestion Control - AIMD
The AIMD approach is that senders can increase rates until packet loss (congestion) occurs, then decrease sending rate on a loss event. This is called Additive Increase and Multiplicative Decrease, resulting in a saw-tooth pattern. this is accomplished by the TCP sender limiting transmission to the $LastByteSent - LastByteAcked \leq cwnd$ where cwnd is dynamically adjusted in response to the observed network congestion.

**Slow Start**
When the connection begins, increase the rate exponentially until the first loss event. Initially `cwnd` is set to 1 MSS, and `cwnd` doubles every RTT (done by incrementing `cwnd` for each ACK received). We then switch from exponential increase when `cwnd` reaches ssthresh, this is a variable that is dynamically adjusted and it's value is set to 1/2 of `cwnd` before a loss event.

**Tahoe (1988)**
- Always cut the `cwnd` to 1 MSS in response to triple dupes or a timeout

**Reno (1990)**
- Cut the `cwnd` to half on a triple dupe
- Cut the `cwnd` to 1 MSS after timeout
# References
[[UDP]]
[[Ports]]
[[Reliable Data Transfer (RDT)]]
[[Pipelined Protocols]]
[[Congestion Control]]
