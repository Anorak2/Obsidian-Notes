
2025-04-26

Tags: [[Security]] [[Applied Cybersecurity]] [[SQL]] [[Database]]
# SQL Injections
The main cause is when some text the user can input gets treated as SQL commands. Most commonly this looks like injecting commands into a web form. One type is where the user doesn't get any information after submitting the form. The other type of injection is non-blind, which is a dumb name but I didn't think of that, where the user does receive information from the database.

## Performing
We can do injections manually using special characters, or we can use some of the tools that are available such as: ```SQLMap```, ```W3AF```, ```OWASP```. 
# References
[[NoSQL Databases]]

