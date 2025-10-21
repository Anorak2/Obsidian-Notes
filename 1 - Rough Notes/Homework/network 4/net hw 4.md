
## B
![[Pasted image 20251010225908.png]]
Fig 1. A picture of my TCP client and TCP server connecting as intended
![[Pasted image 20251010234314.png]]
Fig 2. A picture of my udp client and server working as intended

## C
Running on the same machine I can't really tell any difference though some part of me thinks the UDP is slightly faster. In truth both seem to arrive basically instantly.

## D
![[Pasted image 20251010235132.png]]
For the UDP server I measured an RTT time of about .22ms

![[Pasted image 20251010235032.png]]
For the TCP server I marked an RTT of about .18 miliseconds but I realized this doesn't include the connection time.
![[Pasted image 20251010235331.png]]
On repeat there was a notably longer time when compared to UDP which is good sinc that is what we would expect.


# E
I noticed slightly smaller times in the morning but nothing that seemed particularly notable without looking deeper.