Status: 

Tags: [[Data Structures]]
# Singly Linked List

![[Pasted image 20241113181743.png]]
Linked lists store a value and a pointer that doesn't need to be strictly connected in memory. 
**Sentinel Nodes**
Sentinel nodes are a special type of node that always exists at the front or the back so that we don't have to deal with an annoying special empty case. There's two types of implementations, one with just one sentinel node and a circular list, and another with a sentinel node at the front and the back

**Invariants**
- Sentinel always points to sentinel node
- first node is always at sentinel.next

# References
