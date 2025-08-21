Status:

Tags: [[Data Structures]]
# Disjoint Sets

Disjoint sets are a very simple but sometimes useful data structure, with the basic idea being we have a set of nodes and we want to be able to connect nodes and tell which nodes are connected. To make this even simpler, we only need to store integers since we can map those integers to whatever type we need.

Time complexities of weighted quick union:

| Construct | Connect        | IsConnected   |
| --------- | -------------- | ------------- |
| O(N)      | O($n \log n$ ) | O($n \log n$) |

**Weighted Quick Union (Best implementation**
The list of sets kinda sucked, and quick find is optimized for checking if nodes are connected. What if we could optimize the connect method. The way we can improve this is by turning the index of each value into a pointer, say:
$$[-1, 0,1,-1,0,2,-1]$$
Where each non negative value points to an index, and the benefit of this approach is that all we need to do in order to connect two nodes is to change the value of the root. The problem with this specific approach though is balancing trees since we only get log n with bushy trees. We fix this using Weighted quick union which means storing the size of each tree, and always merging the smaller tree with the larger tree. That last list would look like:
$$[-5,0,1,-1,0,2,-1]$$
We can just store the size of each tree as a negative number to still show that it is a root. If, given this list, we wanted to merge 3 and 0 we could compare which tree is larger (0 in this case) and then simply set arr\[3\] to 0. As a side note, we use weights instead of heights since it has actually been proven to be the same in terms of time complexity, and size is much easier to calculate.

**Naive Implementations**
The worst way to do this would be to store every single edge connecting nodes, which we just do not care about. A better implementation would be to store islands as lists, \[{1,5,3} {2} {4,6}\].

| Construct | Connect | IsConnected |
| --------- | ------- | ----------- |
| O(N)<br>  | O(N)    | O(N)        |

**Quick Find** 
We could, rather than that other stuff, just use an [[Arrays|array]] of integers such as 
$$[4,4,4,5,4,5,6]$$ This is an appealing approach because this operation has an O(1) time for comparison since we can just look at two positions using array lookup and see if the integers match.

| Construct | Connect | IsConnected |
| --------- | ------- | ----------- |
| O(N)      | O(N)    | O(N)        |
# References
[[Arrays]]
