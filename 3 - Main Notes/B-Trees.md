
Tags: [[Data Structures]]
# B-Trees
B-Trees are a form of binary search tree that self balances, ensuring that time complexities remain O(log n). B-Trees are absolutely ubiquitous, and are used as an indexing structure for relational databases and for many file-systems. The reason for this is B-Trees allow for efficient key-value lookups and range queries.

When used in a database B-Trees often break the database down fixed size blocks (or pages), that traditionally are 4 kilobytes. Each page can then refer to another page using memory addresses, which operate like pointers but on disk, which forms a tree of pages.

| Time Complexity | Contains      | Insert        | Delete        |
| --------------- | ------------- | ------------- | ------------- |
| Worst Case      | O($n \log n$) | O($n \log n$) | O($n \log n$) |
**Idea**
The basic idea is to store multiple values inside of each node rather than giving each value it's own location. This approach reduces the number of pointers necessary when compared to a structure like a Red-Black Tree, and sequential reads are generally faster than random reads. This is especially true on storage that still uses HDD's.


![[Pasted image 20241128012130.png]] ![[Pasted image 20241128012146.png]]

This structure works by enforcing a size limit per node, which can vary wildly but for operating systems can number in the thousands. This limit is enforced by splitting a node when it gets too large, similar to how a rotation is performed in other tree structures. This operation may cascade as well if the parent grows too large. This approach **formally guarantees** that B-Trees will remain of `O(log n)` size.

# References
- [[Binary Search Trees]]
- [[Relational Database Model]]