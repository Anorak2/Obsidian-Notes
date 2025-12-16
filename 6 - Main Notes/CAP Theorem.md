Status:

Tags: [[Databases]]
# CAP Theorem

**Consistency**
This is where we have the database in a consistent state, so an example where we care about consistency would be like having a bank account balance. On the other hand, if we don't care that might be say the number of likes on a twitter post.

**Availability**
Availability is making sure we always get a response, even if that means getting an error.

**Partition Tolerance**
Tolerance is how well the system can respond to a node (say a data center) going down.

**C.P.**
	This is best for systems that prioritize consistency of data even if there are network partitions, the trade off is that availability gets sacrificed meaning users might get downtime. A common example would be a financial system to ensure balances remain accurate.

**A.P.**
	This works for systems that prioritize availability and partition tolerance to continue working during a network partition, but they might return stale or inconsistent data. An example would be a social media platform, during a partition the number of likes could be incorrect but the system remains up and running

**C.A.**
	When you build a system that is both consistent and available it won't be able to tolerate system failures well, this means that when a failure occurs the entire system goes down. This only really works for a small system when there is no network issue, but at scale you won't find it since it is very hard to escape failures or partitions

# References
[[Confidentiality, Integrity, Availability]]
