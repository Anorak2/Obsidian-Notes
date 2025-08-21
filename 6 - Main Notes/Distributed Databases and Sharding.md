Status:

Tags: [[Database]] [[Servers]]
# Distributed Databases

By distributing our databases this means that we can store and process data over a connected system of computers at different sites. This is nice because a [[Centralized Database Systems|Centralized System]] has issues as it scales, but using a distributed network we can get more reliability and better performance within a local area.

**Advantages**
- Data is located nearer to where the demand is
- Reduced operating costs
- Less danger of a single point of failure
- Faster data access
- Faster data processing 
- Easier to grow and expand
- Increased Reliability

**Downsides**
- Complexity of management and control
- Security
- Lack of Standards
- Increased storage requirements
- Greater difficulty in managing the environment

**Horizontal Sharding**
Also known as horizontal fragmentation, this is a way of splitting up a database by having different distributed databases have different rows/entities while all still having the same columns

To recreate the table all we need to do is union the results from each system since each carries a subset.

**Vertical Fragmentation**
This is when we divide a relation vertically by the columns and only keeping certain attributes of the relation in each. To recreate the original we need to use a full outer join.

**Hybrid Fragmentation**
Mixing both of the previous two

# References:
[[CAP Theorem]]

[[Database Federation]]
