Status:

Tags: [[Data]]
# ACID

**Atomicity**
Either all operations of the [[Transactions|transaction]] are properly represented in the database or none are.

**Consistency**
When we execute a [[Transactions|transaction]] in isolation it preserves the database consistency 

**Isolation**
Even though we can receive multiple [[Transactions]] and process multiple transactions concurrently we ensure that we always finish one [[Transactions|transaction]] before starting the next.

**Durability**
After processing [[Transactions]] the changes any one of those made to the system persist even if there are system failures

# References
[[Transactions]]
