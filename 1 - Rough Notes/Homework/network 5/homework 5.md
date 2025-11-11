## 1.
A. The main difference between TCP and UDP is that TCP requires that packages are acknowledged and TCP will send these packets over and over again until they are received, to help with this TCP also has several other features to improve reliability such as flow control. UDP on the other hand simply sends the packet with no concern if it arrives and is processed by the receiver.

B. QUIC reduces the setup overhead by including data needed for encryption in the initial setup. QUIC also adds several different flow controlled streams so that if one fails the other data streams can be processed while the broken stream is resent.

C. According to Cloudflare's radar, over the last 12 months worldwide the usage rate of QUIC has been between 34% and 31% as the respective max and min with the majority of traffic being based around TLS 1.3. Despite TLS 1.3 remaining dominant a pretty enormous section of the internet has shifted to using QUIC, perhaps most notably youtube has switched to QUIC for media delivery

https://radar.cloudflare.com/adoption-and-usage?dateRange=52w

## 2.
1 is the 1's complement, and UDP uses this as the checksum in order to reduce the header size. Using 1's complement the receiver will add up every byte in the packet such that sum=1 + 1 = 0 and sum=0+1= 1 etc. A single bit error should always be detected in this version but a 2 bit error very possibly won't be with this checksum model. ex: 1 0 turns to 0 1, or 0 0 turns to 1 1

## 3. 
a. In reliable data transfer protocols we introduce sequence numbers so that if a packet is lost it is immediately obvious due to a break in the sequence

b. We need to introduce timers so that we don't wait endlessly for a packet that was dropped at some previous point and therefore can't arrive

## 5.
a. telnet uses port 23 by default
b.
	  i. source: 192.168.1.3/23   to   dest:192.168.1.1/23
	 ii. source: 192.168.1.2/23   to   dest:192.168.1.1/23
	iii. source: 192.168.1.1/23   to   dest:192.168.1.3/23
	 iv. source: 192.168.1.1/23   to   dest:192.168.1.2/23
	  v. Yes it is possible that the source port numbers are the same
	 vi. if they are running at the same time then they would need to use different ports

## 6. 
1. Something interesting is that the password was transmitted in plain text rather than being hashed first like many other versions. 
![[Pasted image 20251024225241.png]]
2. Just a simple DNS lookup was run, and the ip of the ftp server is 44.241.66.173 as can be seen in any screenshot talking to the ftp server
![[Screenshot from 2025-10-24 22-50-22.png]]
 3. The first "real" TCP segment was identified as the one immediately following the SYN, SYN ACK connection; though I don't really understand why the 2nd ack from my client was considered different from the other two.
![[Pasted image 20251024225425.png]]
 4. The SYN flag is set in the first one, the second one had the Syn and Ack flags set, and the third on had the ACK set
![[Pasted image 20251024225812.png]]
![[Pasted image 20251024225946.png]] ![[Pasted image 20251024230009.png]]
5.  The connection terminates with the FIN ACK, ACK pattern that we learned about in class which is very cool to see in the wild as a sanity check of my knowledge
![[Screenshot from 2025-10-24 23-01-00.png]]