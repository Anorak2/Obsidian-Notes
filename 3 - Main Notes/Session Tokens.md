
2026-05-11

Tags: [[Web]] [[Networking]] [[Networking]]
# Session Tokens
encoding state into URL's can be useful for certain applications however for others it is a very bad idea. URL's are vulnerable to eavesdropping, especially If HTTP mixed used with HTTPS, and it makes the Session Fixation attack easier. URL's are also unstable. This is fine for a one time share, but for something like a shopping cart this is horrible.
![[Pasted image 20260511191755.png]]

What should be included in the token?
Option 1: Minimal client-side state
- Token = random, unpredictable string
	- Just an ID → No data embedded
	- Store all data associated with the session at server → Server overload
Option 2: More client-side state
- Token = [ user ID, expiration time, access rights, last login, user info … ]
	- Client should not be able to tamper with the token → HMAC(server key, token)
	- Sever still maintains some state (e.g., logout state)

## Storing Session Tokens
Embed in URL links
- `https://site.com/checkout?SessionToken=kh7y3b`
- Token leaks via HTTP Referer header
Store in a hidden form field
- `<input type=“hidden” name=“sessionid” value=“kh7y3b”>`
- Only works for short sessions 
Store in browser cookie
- `Set-Cookie: SessionToken=fduhye63sfdb`
- Browser sends cookie with every request, even if request not initiated by the user (CSRF attacks)

# References
- [[Web Cookies]]