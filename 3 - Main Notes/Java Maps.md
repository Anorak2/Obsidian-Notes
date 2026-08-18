
2026-06-15

Tags: [[Software Engineering (SWE)]] [[Java]]
# Java Maps
In Short if you need \_\_\__:
- No order -> `HashMap`
- Insertion order -> `LinkedHashMap`
- Sorted Order -> `TreeMap`
- `HashTable` is synchronous but slow (locks whole table) and legacy

**HashMap**
HashMap offers 0(1) lookup and insertion. If you iterate through the keys, though, the ordering of the keys is essentially arbitrary. It is implemented by an array of linked list.

**Linked Hash Map**
`LinkedHashMap` offers O(1) lookup and insertion. Keys are ordered by their insertion order. It is implemented by doubly-linked buckets.

**Tree Map**
`TreeMap` offers O(log N) lookup and insertion. Keys are ordered, so if you need to iterate through the keys in sorted order, you can. This means that keys must implement the Comparable interface. `TreeMap` is implemented by a Red Black Tree. 


**Legacy: Hash Table**
A `Hashtable` is an array of list. Each list is known as a bucket. The position of bucket is identified by calling the `hashcode()` method. A `Hashtable` contains values based on the key.



# References
- [[Java HashMap Internals]]
- [[Red Black Trees (LLRB)]]