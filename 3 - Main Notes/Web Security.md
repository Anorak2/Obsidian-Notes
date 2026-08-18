
2026-05-11

Tags: [[Networking]] [[Networking]]
# Web Security
## Basic Review
![[Pasted image 20260511184910.png]]
How do HTTP server interacts with web applications?
- CGI: The Common Gateway Interface
- FastCGI: a variation of the CGI, faster
- Modules: directly execute script-based programs
![[Pasted image 20260511185134.png]]

## Common Attacks
**CSRF – Cross-site request forgery**
- Bad website sends request to good website, using credentials of an innocent victim who “visits” the bad site
**XSS – Cross-site scripting**
- Attacker inserts client-side script into pages viewed by other users, script runs in the users’ browsers
**SQL Injection**
- Browser sends malicious input to server
- Bad input checking leads to malicious SQL query

**HTTP Auth**
This is a form of basic HTTP based authentication considered secure only when used with TLS. The browser sends a basic request, server sends HTTP 401 Unauthorized with  Authentication “realm” (description of system being accessed) and the user logs in. From there the browser uses the hashed password (H3) for all subsequent HTTP requests. Due to a number of issues this version of auth is almost never used

Problems include
- User can only log out by closing browser
- What if user has multiple accounts?
- What if multiple users of the same browser?
- Site cannot customize password dialog
- Easily spoofed


# References
- [[HTTP]]
- [[Web Cookies]]