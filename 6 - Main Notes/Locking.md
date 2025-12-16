Status:

Tags: [[Databases]]
# Locking

Locking is a way of dealing with [[Concurrency Control|Concurrency Problems]] and when a transaction needs some assurance that the object its interested in will not change in some unpredictable way it puts a lock on that object to prevent other [[Transactions]] from messing with it

**Exclusive locks (X locks)**
Exclusive locks makes it so that no other transaction can do any operations on the object while the lock is placed.

**Shared locks (S locks)**
This is a level that lets other shared locks do their operations, but prevents exclusive lock operations from doing their thing.

# References
[[Transactions]]

[[Concurrency Control]]