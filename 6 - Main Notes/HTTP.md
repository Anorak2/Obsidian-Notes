
2024-12-24

Tags: [[Programming]] [[Web]] [[Networking and Network Security]]
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

## Response Codes
| Class | Meaning                |
| ----- | ---------------------- |
| 1xx   | Informational Response |
| 2xx   | Success                |
| 3xx   | Redirection            |
| 4xx   | Client Error           |
| 5xx   | Server Error           |

| Code |                       | When to use                                                                                                    |
| ---- | --------------------- | -------------------------------------------------------------------------------------------------------------- |
| 200  | Ok                    | Standard response for successful queries                                                                       |
| 201  | Created               | Accepted, resource was created                                                                                 |
| 202  | Accepted              | Accepted but not created yet                                                                                   |
| 204  | No content            | Good response but nothing to be returned                                                                       |
| 301  | Moved Permanently     | Used to be there but now can be found at another URL                                                           |
| 303  | Redirected            | redirects client to a different URL                                                                            |
| 400  | Bad Request           | The client sent a malformed HTTP request                                                                       |
| 401  | Unauthorized          | Similar to 403 but for when auth is required and it<br>has either failed or wasn't provided                    |
| 403  | Forbidden             | Valid request but the user isn't allowed to perform <br>this action. Ex: you can be logged in but not as admin |
| 404  | Not Found             |                                                                                                                |
| 500  | Internal Server Error | Valid request but the server failed to process it                                                              |
| 501  | Not Implemented       | When the feature hasn't been programmed yet                                                                    |
| 502  | Bad gateway           | Server was acting as a proxy and there was an <br>upstream error                                               |
| 503  | Service Unavailable   | Usually temporary, like when the site is overloaded                                                            |
| 504  | Gateway Timeout       | Server was acting as a proxy and an upstream <br>connection timed out                                          |
# References
[[HTTP status codes]]

[[HTTP in Go]]

[[TCP]]
