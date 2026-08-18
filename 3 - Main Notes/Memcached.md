
2026-07-17

Tags:
# Memcached
Memcached is an in-memory key-value store originally written in Perl and later rewritten in C. It is used by many companies for it's sort of pure simplicity when compared to many other tools. It does very little other than one thing: it provides an in memory key-value store.

Memcached is used as a cache for slow database queries or HTTP responses that are expensive to compute. However, Memcached is only meant to be used as a last resort for our application. What this means is that we should never expect our values to be present in memory, it is more of a "happy surprise" if they are. Otherwise caching in this instance becomes a cop-out for performance, like duct-tape over a problem.

 Memcached is a good choice for caching expensive queries, but it should not be relied on for persistent or durable storage. Always build your application around Memcached not having what you want. Plan for the worst, hope for the best.
## Architecture
Keys in Memcached are strings, and they are limited to 250 characters. Values can be any type, but they are limited to 1 MB by default. Keys also have an expiration date or time to live (TTL). However, this should not be relied on, as the least recently used (LRU) algorithm may remove expired keys before they are accessed.

**Memory Management**
In order to prevent fragmented memory, Memcached operates by allocating some amount of space from the operating system. The operating system thinks that Memcached is using this memory, but it may not be storing anything in it. This memory is cut up into pages, and the pages into equal sized Chunks. The chunk has a fixed size determined by the slab class. A slab class defines the chunk size, for example, Slab class 1 has a chunk size of 72 bytes while Slab class 43 has a chunk size of a `1MB`. 

Each item has a key-value pair, and some metadata. This Item is stored inside the closest chunk size to the item's size. For example, if the item size is 40 bytes in size, a whole chunk is used to store the item. The closest chunk size to the 40-byte item is 72 bytes, which is slab class 1, leaving 32 bytes unused in the chunk. That is why the client should pick items that fit nicely in chunks, leaving as little unused space as possible.

As items are allocated memcached forces to be next to eachother in the page, avoiding memory fragmentation.


**LRU**
As the memory eventually fills up, Memcached uses a linked list LRU to release items when memory is full. Every slab has it's own individual LRU list. No two threads can update the same data structure concurrently. To solve this, the thread that needs to update any data structure in memory must obtain a mutex, and other threads wait for the mutex to be freed. This is the basic locking model, and it is used in all applications. Memcached is no different from the LRU data structures. Originally this lock was global, but it was updated to be per slab class.

**Collisions**
Because hashing maps keys to a fixed size, two keys may hash to the same index, causing a collision. Let’s say I’m going to write a new key called “What”. The hash of “What” collides with another existing key.

 To solve this, Memcached makes each index in the hash table map to a chain of items as opposed to the item directly. We add the key “What” to the chain, which now has two items. When the key is read, all items in the chain need to be looked up to determine which one matches the desired key, giving us a O(N) at worst case. If the performance of the reads starts to decrease, Memcached does a hash resize and shifts everything around to flatten the structure down.

## Example
This is a simple example that sets a key on a distributed set of servers running memcached.
```js
const MEMCACHED = require("memcached");
const serverPool = new MEMCACHED(["hostname:11211", 
"hostname:11212",
 "hostname:11213",
 "hostname:11214"]);
function run() {
 [1, 2, 3, 4, 5, 6, 7, 8, 9].forEach(a => serverPool.set("foo" + a, "bar" + a, 3600, err => console.log(err)))
}
run();
```
 
# References
- [Hussein Nasser's Substack](https://open.substack.com/pub/hnasr/p/memcached-architecture?r=6lwxzz&utm_campaign=post&utm_medium=web)
- Designing Data Intensive Applications
- [[Singly Linked List*]]
- [[Mutex Locks and Semaphores]]
- [[Hash Tables - Hashmaps]]