
2024-12-24

Tags: [[Programming]] [[Web]]
# HTTP Requests
![[Pasted image 20241224154851.png]]

```
	GET /18_http.html HTTP/1.1  
	Host: eloquentjavascript.net  
	User-Agent: Safari/537.36
```
What a sample get request might look like, GET is the specific method used here. There are a bunch of other methods, some common ones including DELETE, PUT, and POST which function similar to the [[CRUD]] operations. We can delete a resource, put which is to create or update a resource, post to send information, and get to request information.

After the method, there is the path to the resource that the command applies to. What we are requesting etc. Last part of the first line is the protocol version since all good protocols should include that, 1.1 works but now a lot of websites will use HTTP 2, in practice there is a lot of overlap and browsers automatically switch versions.

```
	HTTP/1.1 200 OK  
	Content-Length: 65585  
	Content-Type: text/html  
	Last-Modified: Mon, 08 Jan 2018 10:29:45 GMT  
	<!doctype html>  
	... the rest of the document
```
This is a sample response from the server, it starts with the version and then the [[HTTP status codes|status code]] from the server, and then as a human readable string.

## HTTP 2
HTTP 2 is also based on TCP but it keeps a persistent connection between the client and the server the reduce friction. HTTP 2 also adds some other features such as allowing for the server to push packets to the client without the client requesting them first.


## HTTP 3
HTTP/3 runs on top of the ```QUIC``` transport protocol which is based on UDP, this is because in a vanilla TCP connection there is no security and also


# References
[[HTTP status codes]]

[[HTTP in Go]]

[[TCP]]
