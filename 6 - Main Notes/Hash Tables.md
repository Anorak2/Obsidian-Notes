Tags: [[Data Structures]]
# Hash tables

The basic idea behind hash tables is, what if we used data as an index rather than storing the data itself? This is a very strange idea, but using [[Hashing]] it actually becomes not that crazy of an idea. This works because by hashing it means we don't have any more overflow problems, and any problems we have with data matching are more or less resolved.

**Separate Chaining Data Indexed array**
The idea here is that rather than just having [data] -> [T/F], what if instead we had data point to a list of values since that way we don't have to worry about hash codes matching eachother. This implementation has an interesting runtime,

| Worst Case Time   | Contains | add  |
| ----------------- | -------- | ---- |
| Separate chain... | O(Q)     | O(Q) |
This is because instead of being constant, Q is the size of the longest list present. This really isn't that much of a problem though, and in fact the features we gain are much better. This is because we can take our hash codes and do a modulus function (say 10) when we have a low amount of items, and this means we can fit all of our values into only 10 buckets. We can do this dynamically too, and what this means is that we can scale the size of our hash table to meet the requirements, and as long as we keep scaling it then we can maintain a very close to O(1) performance. We do this by calculating a load factor, the number of items divided by the number of buckets, and when it is over a certain size then we can geometrically increase the number of buckets.

# References
[[Arrays]]

[[Hashing]]