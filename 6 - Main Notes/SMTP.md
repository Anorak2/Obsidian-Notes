
2025-09-10

Tags: [[EECS 563 - Intro to Comm Networks]] [[Networking]]
# SMTP
Email has three major components: user agents, mail servers, and Simple Mail Transfer Protocol (SMTP). It is defined in RFC 821.

**User Agent**
The user agent handles the composing, editing, and reading of emails.

**Mail Servers**
Mail servers handle the routing done on the back end. This means the mailbox for the user, the message queue of outgoing emails, and the SMTP protocol between mail servers.

**SMTP**
The client (server sending the email) uses TCP to connect to the receiving server on port 25 afterwards the sending server directly transfers. The transfer has three stages: the handshaking, transfer of messages, and closure.

## Mail Message Format
The format is defined of the header lines such as to, from, subject, followed by a blank line and then the body of the email. The body is supposed to be ASCII characters only and it is defined in RFC 822.

# References

