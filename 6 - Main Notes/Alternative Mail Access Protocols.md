
2025-09-10

Tags: [[EECS 563 - Intro to Comm Networks]]
# Alternative Mail Access Protocols
While SMTP is likely the oldest mail protocol, others such as POP3 and IMAP also exist as alternatives.


**POP**
Known as the Post Office Protocol, it's defined in RFC 1939. It uses a "download and delete" mode which means the server is only used for routing, it doesn't keep any copies.

**IMAP**
The Internet Mail Access Protocol (RFC 3501) added more features and the manipulation of stored messages on the server such as retrieval, deletion, and foldering. IMAP keeps all of the messages in one place, on the server, and it allows users to organize messages in folders. IMAP also keeps the user state across sessions.

**POP3**
This protocol is very similar to POP but it uses a "download and keep" model instead 


**HTTP**
Many services added a web component that provides a web interface as a user agent on top of SMTP to send messages and IMAP (or POP) to retrieve messages.




# References
[[SMTP]]