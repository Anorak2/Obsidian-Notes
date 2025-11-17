# 1
- a: The IP protocol and DHCP
- b: as part of the IP datagram it has a section for the upper layer protocol, ie TCP or UDP.
- c: 11011111.00000001.00011110.00011001
- d: Yes, the version, source address, destination address, and the length
- e: If the router only has one IP address then it would have to use NAT to transfer data to each of the computers connected to the router. Each of these PC's use the same IP as the router but with different port numbers used to designate which PC.
# 2
Initial:
### A

| Variable    | Distance |
| ----------- | -------- |
| y (Current) | 0        |
| z           | inf      |
| x           | inf      |
| v           | inf      |
| w           | inf      |
| u           | inf      |
| t           | inf      |
updates to 

| Variable         | Distance |
| ---------------- | -------- |
| y                | 0        |
| z                | 12       |
| x (next current) | 6        |
| v                | 8        |
| w                | inf      |
| u                | inf      |
| t                | 7        |
Updates to 

| Variable         | Distance |
| ---------------- | -------- |
| y                | 0        |
| z                | 12       |
| x                | 6        |
| v                | 8        |
| w                | 12       |
| u                | inf      |
| t (next current) | 7        |
Updates to:

| Variable | Distance |
| -------- | -------- |
| y        | 0        |
| z        | 12       |
| x        | 6        |
| v        | 8        |
| w        | 12       |
| u        | 2        |
| t        | 7        |
Now we're finished
### B

| Variable    | Distance |
| ----------- | -------- |
| y           | inf      |
| z           | inf      |
| x           | inf      |
| v           | inf      |
| w           | inf      |
| u           | inf      |
| t (current) | 0        |


| Variable         | Distance |
| ---------------- | -------- |
| y                | 7        |
| z                | inf      |
| x                | inf      |
| v                | 4        |
| w                | inf      |
| u (next current) | 2        |
| t                | 0        |
Updates to 

| Variable         | Distance |
| ---------------- | -------- |
| y                | 7        |
| z                | inf      |
| x                | inf      |
| v (next current) | 4        |
| w                | 5        |
| u                | 2        |
| t                | 0        |
Updates to 

| Variable | Distance |
| -------- | -------- |
| y        | 7        |
| z        | inf      |
| x        | 7        |
| v        | 4        |
| w (next) | 5        |
| u        | 2        |
| t        | 0        |
Updates to 

| Variable | Distance |
| -------- | -------- |
| y        | 7        |
| z        | inf      |
| x (next) | 7        |
| v        | 4        |
| w        | 5        |
| u        | 2        |
| t        | 0        |
Updates to 

| Variable | Distance |
| -------- | -------- |
| y        | 7        |
| z        | 15       |
| x        | 7        |
| v        | 4        |
| w        | 5        |
| u        | 2        |
| t        | 0        |
and we're done

# 3
### A: 
- 
	-s means show statistics for each protocol, where we can clearly see the breakdown for each individual protocol. 
	![[Pasted image 20251113222440.png]]
	-l shows the processes currently listening and their ports, in the example you can clearly see all of the processes that are listening to various ports on my computer
	![[Pasted image 20251113222734.png]]
	-i shows the breakdown by interface, in my example wlp3s0 is clearly the main interface I use
	![[Pasted image 20251113222900.png]]
### B
![[Pasted image 20251113223407.png]]
it's interesting that it shows the DNS server and the ip6/ip4 addresses. It also shows the hardware address as a unique identifier.
# 4
### A
![[Pasted image 20251113223615.png]]
It was able to detect the city of my device 
![[Pasted image 20251113223700.png]]
![[Pasted image 20251113223721.png]]
However it wasn't able to find the IP addresses of several websites that I know the location of, the reason why is because the server is configured with cloudflare tunnels so all of the traffic appears to come through cloudflare meaning the results appear local.

### B
You could use such a service to crack down on political dissidents and protesters in an authoritarian country.

If a stalker was able to get someone to accidentally click on a link a service such as that would allow them to greatly narrow down their search and continue stalking them.

# Wireshark Lab
1. UDP
2. 
![[Pasted image 20251113225917.png]]
How I read this is that my computer was looking to find a DHCP server willing to give it an IP address, then the router (local in this case) offered it's services, then the virtual machine requested a specific IP address, and lastly the router acknowledged that request as valid granting the IP.
3. 
   Discover: 0.0.0.0/68 -> 255.255.255.255/67
   Offer: 192.168.122.1/67 -> 192.168.22.57/68
   Request: 0.0.0.0/68 -> 255.255.255.255/67
   ACK: 192.168.122.1/67 -> 192.168.122.57/68
4.  The only difference I could find was that option 53 was set differently
![[Pasted image 20251113232611.png]]
5.  
    Discover: 0x6d36642
    Offer:  0x6d36642
    Request:	 0x6d36642
    ACK: 0x6d36642
	The purpose of the transaction ID field to establish the line of communication since the sender might not have an IP address yet, since UDP the transaction ID can establish a link between different dhcp messages and is useful if a packet is lost.
6. 192.168.122.1 since that is the IP sending the responses, when the virtual machine is sending requests to 255.255.255.255 that is just broadcasting on the local network to ensure all machines receive it. that first address also shows up in several of the DHCP packets as the DHCP Server Identifier
7. In the offer it says `Your(Client) IP Address:192.168.122.57`. This IP is also used later as the source of the release reaffirming that this is what the router assigned.
8. The purpose of a lease time is reuse addresses after devices are inactive or leave the network. in my experiment the lease time was 1 hour 
   ![[Pasted image 20251113233250.png]]
   
