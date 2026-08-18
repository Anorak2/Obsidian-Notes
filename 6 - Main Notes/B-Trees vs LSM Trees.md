
2026-07-17

Tags: [[Designing Data Intensive Applications]] [[Data]]
# B-Trees vs LSM Trees
Fundamentally the difference between the two structures is whether we choose append only logging or update in place. Both keep logs, for B-Trees all data must be written twice, first to a Write Ahead Log (WAL), and then to the tree in order to maintain resiliency in case of sudden power failure/shutdown. LSM Trees aren't above this either though, since log structured implementations rewrite data multiple times due to the merging process.

Typically, log structured storage is able to sustain a much higher throughput of random writes than B-Trees are able to. Likewise, B-Trees are thought to be faster for reads. In practice it is dependent on the work being done, so if performance is critical multiple databases should be tested. B-Trees are better normalized than log structured approaches, allowing relational databases to isolate transactions by placing locks on a range of keys directly inside of the tree.

 A stack is a last-in, first-out (LIFO) data structure that provides efficient O(1) push and pop operations, but it only allows access to the most recently added element.

A stack is a data structure that operates inversely to a queue, where the last element inserted is the first element to be removed.

A stack is a powerful, simple structure that allows us to add or remove items in a LIFO ordering; This can be powerful for many cases, including algorithms where certain parts of the data reduces out.
# References
- [[B-Trees]]
- [[LSM Trees]]
- [[Database Locking*]]