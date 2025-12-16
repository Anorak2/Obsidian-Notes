
2025-01-13

Tags: [[Programming]] [[Servers]] [[Databases]]
# Three Layer Architecture
The basic idea behind a three layer structure is that we want to limit the permissions of users and design our software in a scalable way.

**User Layer**
This is where, well, the users exist and all of the client side stuff can happen

**Application Layer**
All of the communication between users and the database layer pass through this tier. Here information can be processed and all of the server side stuff is done.

**Database Layer**
This is where data can be stored by the application and managed.

## Benefits
The benefits include scalability, since any tier can be scaled independently. Since each tier is somewhat independent this means that they can also be developed simultaneously allowing for faster development. There are also reliability benefits since one layer going down can be independent from the other two layers. Lastly there is the security aspects, which I believe is one of the best reasons, since we can prevent the users from directly interacting with the database and the application layer can police any activity. 
# References

