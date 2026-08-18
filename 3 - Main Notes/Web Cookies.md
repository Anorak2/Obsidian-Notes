
2026-05-11

Tags: [[Web]] [[Networking]] [[Networking]]
# Web Cookies
HTTP is a stateless protocol, so use cookies to add/maintain state where a cookie is a file created by a website to store information in the browser.  When a browser first connects to a web server, it has no cookie for that server. When web server responds, it includes a Set-Cookie header that defines a cookie. Each cookie is a name-value pair. When browser connects to the web server again, it includes the cookie <name, value> pairs contain information that the server can use to connect related requests.

HTTP Header:
Set-cookie:
> NAME=VALUE ;
> domain = (hosts);
> path = (URL);
> secure = (only send over HTTPS);
> expires = (when expires);
> HttpOnly

- Domain and path inform the browser about which sites to send this cookie to
- Secure cookie: can only be sent when the request is made using SSL
- Expires: The maximum lifetime of the cookie, If not specified, it means for the current session only
- `HttpOnly`: cookie can only be sent by browser, but cannot be accessed by Javascript
- `Samesite`: can be `[strict, lax, none]` and it helps to enhance security against CSRF attacks. The `strict` value will prevent the cookie from being sent by the browser to the target site in all cross-site browsing contexts, even when following a regular link. Under the strict value if I clicked a link to a website like a private github repository, then github wouldn't be sent the cookie and I wouldn't be able to access the repo. The `lax` value is a balance between security and usability, in that same scenario as above the github website would receive the cookie but not for methods prone to CSRF attacks like `POST`.  `none` offers no such protections.

Client side cookies can be easily set, for example in javascript
```document.cookie = “name=value; expires=…; ”```
## Security
Two important issues:
1. What scope a server may set for a cookie? A cookie domain is any domain-suffix of URL-hostname, except top-level domain (TLD) examples include `login.site.com` and `.site.com`. The path can be anything
2. When is a cookie sent to a URL? The browser sends all cookies in URL scope cookie-domain is domain-suffix of URL-domain, AND cookie-path is prefix of URL-path, AND `[protocol=HTTPS if cookie is “secure”]`. This is to ensure that the server only sees cookies in its scope. For example A cookie with `domain = example.com`, and `path = /some/path/` will be included in a request to: http://foo.example.com/some/path/subdirectory/hello.txt

## Use Cases
Personalization
- Helps the website recognize the user from a previous visit
Authentication
- Cookie proves to the website that the client previously authenticated correctly
Tracking
- Follows the user from site to site
- Learns his/her browsing behavior, preferences, and so on

## Tracking 
How can a third-party plant the cookie in your browser and later retrieve them?
- E.g., use an image`<img src="http://doubleclick.net/ad.gif" width=1 height=1>`. Each webpage contains an image from doubleclick and the same cookie is set when the image is loaded.
 ![[Pasted image 20260511193714.png]]
 When browser visits another website with the same tracker image
- Browser sends the `cookie = abc`
- `DoubleClick` can tell the user’s identity from the cookie
## Evercookies (Respawning)
Evercookies use multiple storage vectors to store content
- E.g., Flash cookies, localStorage, sessionStorage, Etags
- Cookie respawning is to regenerate previously removed HTTP cookies using evercookies. This way if a user deletes their cookies they can still be tracked since it comes right back.

# References
- [[HTTP]] 
- [[Session Tokens]]
- [OWASP: Samesite](https://owasp.org/www-community/SameSite)
- [[CSRF Attacks*]]