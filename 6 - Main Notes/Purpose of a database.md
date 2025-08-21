Status:

Tags: [[Database]]
# DB Purpose

Atomicity of Updates
- Failures may leave database in an inconsistent state with partial updates carried out
- Atomicity means everything happens or nothing happens
- Example: Transfer of funds from one account to another should either complete or not happen at all

Concurrent access by multiple users
- Concurrent access needed for performance
- Uncontrolled concurrent accesses can lead to inconsistencies
- Ex: Two people reading a balance (say 100) and updating it by withdrawing money (say 50 each) at the same time
Security 
- Here to provide user access to some but not all of the the data

**Databases exist to provide solutions to all of those problems**

Databases should also provide users with an abstract view of the data and allow for data modeling and data abstraction

# References
