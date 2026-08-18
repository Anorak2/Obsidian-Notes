
2026-04-14

Tags: [[Languages]]
# Java HashMap Internals
```java
class Node<K, V> {
	int hash;
	K key;
	V value;
	Node<K, V> next;
}
```
Internally the Java HashMap is an array of nodes where each node stores a key value pair, in the case of collision then it will store the next node as well.


```java
index = hashCode(key)  & (n - 1)
```
Hashcode is used in the bucket generation as follows. n is the number of buckets, with the default value at initial startup. The reason there is a bitwise and is to reduce the number of bits without having to use a modulo operator, and intuitively this makes sense since N should always be a power of 2.

```java
static final int hash(Object key) {
    int h;
    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
}
```
To generate a hash, there is a hash() function that looks like the one above. So first, if the key is null it returns 0.  A comment breaking it down is below, but ultimately it is about ensuring the high order bits affect the low order bits since we will sort based on those lower order bits. This isn't super common, so the java developers chose to do this spreading in "the cheapest possible way."

>  Computes key.hashCode() and spreads (XORs) higher bits of hash to lower. Because the table uses power-of-two masking, sets of hashes that vary only in the higher bits would otherwise collide. (Among known examples are sets of Float keys holding consecutive whole numbers in small tables.) So we apply a transform that spreads the impact of higher bits downward. There is a tradeoff between speed, utility, and quality of bit-spreading. Because many common hash sets are already reasonably distributed (so don't benefit from spreading), and because we use trees to handle large sets of collisions in bins, we just XOR some shifted bits in the cheapest possible way to reduce systematic lossage, as well as to incorporate impact of the highest bits that would otherwise never be used in index calculations because of table bounds."

## Multi-threading
HashMap by default isn't able to handle concurrency, and it is even supposed to be possible for get() to fall into an infinite loop due to having only a partially updated view. If a thread safe hashmap is needed then out of the box we can use `java.util.concurrent.ConcurrentHashMap` which implements the Map interface in a safe way, using the same Node array/bucket architecture. From java 8 onwards this implementation uses CAS (Compare-And-Swap) operations for atomic updates with fine-grained synchronization only when required, but this means no global locking of the interface.
# References
- [[Hash Tables - Hashmaps]]
- [Baeldung Concurrent Map](https://www.baeldung.com/java-concurrent-map)
