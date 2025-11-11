# 1.
	a. Slow start appears to be happening between 0 and 6, and then 23 on at the end
	b. This happens when the window size halves, noticeably around number 15
	c. the 16th round seems to be from a triple ack
	d. the 24nd as the result of a timeout
	e. 1
	f. the image makes it hard to tell but around 22-23
	g. about 2
	h. the 7th round
	i. The congestion window would be set at 8 which would also be the value of ssthresh

# 2.
	a. in this case none of the prefixes match so it would be categorized as other
	b. Since this datagram matches the second prefix it would be sent to link interface 1
	c. This datagram would be sent to link 3 since it doesn't match prefix 1 or 2, and prefix 4 is longer than prefix 3

# 3.
	a. 25
	b. The ack number would be 0, or more accurately whatever the last ack'd number was

# 4.
	a. The network layer transports a segment from sending to receiving hosts, but specifically forwarding and routing. forwarding is moving the packet from the correct input link to the correct output link whereas routing is the pathing that it takes to get there.
	b. The network layer doesn't know that it needs to pass to TCP, it will just deliver the datagram to the specific IP/port and it's job is done
	c. The TCP segement will add about 20 bytes of overhead and then the IP format will add another 20 bytes of overhead onto that, so of each segment 50% will be overhead and 50% will be application data.
	d. In this case the datagram would have to be broken in 6 segments, and the most relevant field regarding fragmentation is the dont fragram (DF) bit that prevents any router at any point from fragmenting the datagram.

# 5
![[Pasted image 20251101203810.png]]
	a. The ip from my computer is 192.168.122.56
	b. The ip from the speedtest.tele2.net is 90.130.70.73 as confirmed by tracing the dns query
	![[Pasted image 20251101204122.png]]
		c. The relative is 0; the raw is 1,566,414,356 (see above)
		![[Pasted image 20251101204343.png]]
		d.  Again the relative is 0, in this case the raw is 65,113,296 (see above)
		e.
		![[Pasted image 20251101204746.png]]
		f. The relative sequence number is 1,048,353
		![[Pasted image 20251101205040.png]]
		g. This is actually really cool to see the raw graph, we can clearly see the slow start from around 0 until what looks like around 1.9s. We can also see what looks to be congestion avoidance at ~2.1 seconds in.