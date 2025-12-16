Status:

Tags: [[Databases]] 
# Transactions

A transaction is just an executing program that forms the unit for database processing. These can be read only or write only transactions, they can also request [[Locking|locks]] to prevent anomalies.

![[Pasted image 20241218224707.png]]

**Commit, Partially Committed, and Aborting**
The running transaction is called the active transaction, and when that transaction is executed successfully it is then committed. A transaction that doesn't complete successfully is considered aborted. if it hasn't been fully committed yet then it is considered partially committed.

When a transaction is committed that means its effect is recorded permanently in the database, whereas an aborted transaction does not affect the database. There's a bunch of types of transaction failures including: Computer failures, transaction or system error, local errors or exception conditions detected by the transaction, disk failure, physical properties or catastrophes. 

# References
[[Concurrency Control]]

[[Locking]]