
2026-05-18

Tags: [[Web Security]] [[Network Security]]
# CSRF Attacks
A Cross-Site Request Forgery (CSRF) is an attack that forces an end user to execute unwanted actions on a web application they're authenticated for. Typically done by methods such as sending a link via email or chat, an attacker may trick the users of a web application into executing actions of the attacker’s choosing. If the victim is a normal user, a successful CSRF attack can force the user to perform state changing requests like transferring funds, changing their email address, and so forth. If the victim is an administrative account, CSRF can compromise the entire web application

## Methods that Do Not work
- Using a secret cookie - it will still be sent on all request
- Only accepting post requests - unfortunately even if the user isn't using a `GET` directly on a link a CSRF can still be forged
- Multi-Step Transactions - As long as an attacker can predict or find out each step of the completed transaction, then CSRF is possible
- HTTPS - only useful for preventing man in the middle attacks, though of course it should be used

# References
- [[HTTP]]
- [[HTTPS Security*]]
- [[XSS Attacks*]]
- 