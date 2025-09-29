1.
	a: $1- (1-p)^{(h+d)}$
	b:  data throughput:
$$T(x)=d\cdot (\frac{C}{h+d} \cdot (1-p)^{h+d})$$
This roughly translates to the number of data bits per packet multiplied by the total number of packets we can send per second times the likelihood that a packet will succeed.
	c:
$$\frac{d}{d \space  d}T(d)=\frac{d}{d \space d}(d\cdot (\frac{C}{1000+d})\cdot (1-.00001)^{1000+d})$$
honestly, this derivative isn't worth solving. I'd rather lose the points. I suspect my function is wrong, but I think it seems solid hence the impasse. 

2.
	a:
	$$\frac{10,000}{1,000,000}s+.001s+\frac{10,000}{2,000,000}+.002s = 18ms$$
	b:
		so long as the buffer is large enough, and the device transmits with no delays in between I see no reason for it to change the time to send$$18ms$$

3.
	a:
		T, but I think it depends on how the webpage is configured. If I made my images source from another site like wikipedia then this likely would be true.
	b:
		False, each http request should be a unique TCP request
	c:
		False, the date header shows the time the message was created. The object's date should likely be passed in as metadata, ie part of the object.
	d:
		False, the message body is optional. I believe this is shown in many GET requests such as loading a webpage

4.
	a: DNS is used to perform a lookup on the url
	b: when the user wants to execute a purchase that data can be POSTed to the server for validation, storage, etc.
	c: Web caching is when some of the websites assets are stored on the users computer, this means that if the user frequents the website the page response times should improve since they need to hit the server less. Not all elements will be cached, often because those elements are frequently updated.

5.
	 DNS, TCP, MDNS, TLSv1.2
	 ![[Pasted image 20250919225356.png]]
	b: 192.168.122.56 for my host; 199.204.169.222, 8.28.7.82 as a couple of the destinations
	![[Pasted image 20250919230054.png]]

6:
	a: 8 seconds
	b: HTTP 1.1 for both
	c: 192.168.122.56
	![[Pasted image 20250919230940.png]]
	d: 200
	![[Pasted image 20250919230952.png]]
	E: Yes I am able to observe the 404 error
	![[Pasted image 20250919231322.png]]
	F:
	![[Pasted image 20250919231508.png]]