Status: 

Tags: [[Database]] [[Servers]]
# Concurrency Control

Concurrency control is needed since transactions submitted by various users may execute and these users can access and update the same items.

#### Common Problems
**Lost Update Problem**
This occurs when an otherwise successful update of a data item by a [[Transactions|transaction]] is overridden by another one that wasn't "aware" of the first one

**The Uncommitted dependency problem**
This problem occurs if a transaction reads one or more data items that are being updated by another transaction, that hasn't been committed next. 

**Inconsistent Analysis Problem**
This problem is when a transaction reads the partial results of another transaction of another transaction that interacts with the same data items. This causes an inconsistent database state

**Unrepeatable Read Problem**
This happens when two or more operations read different values for the same variable. This could like like $T_1$ reads, $T_2$ reads, $T_1$ writes, $T_2$ reads; which results in an inconsistent state 

**Serializability**
Serializability ensures that when multiple transactions execute concurrently, the final result is that same as if they had executed one after another (serially) in some order. Some ways to achieve serializability include timestamp ordering, [[Locking]], and Optimistic concurrency control which checks for conflicts only at commit time.

# References
[[Transactions]]

[[Locking]]