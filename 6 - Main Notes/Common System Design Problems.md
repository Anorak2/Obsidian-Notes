
2026-07-04

Tags:
# Common System Design Problems
## Read Heavy Application
This is for when we have a large number of reads and a relatively static number of writes or changes. A good example would be a news organization with a small team of editors and millions of readers. 

**Solutions**
- Caching. This should occur at various levels including at the CDN level, using tools such as Redis and Memcache, and more such as. Database read replicas to prevent unnecessary database calls

**Failure Modes**
- Cache stampede/thundering herd - cache entry expires, thousands of concurrent requests all miss simultaneously and hammer the DB. Fix: locking/mutex on cache population, or staggered TTLs.
- Hot key problem - one key (celebrity profile, viral product) gets so much traffic a single cache node/shard can't handle it even with caching in place. Fix: replicate that specific key across multiple nodes, or add local in-process caching in front of Redis.
- Cache invalidation - the classic hard problem. TTL-based (simple, but stale window) vs event-based invalidation (accurate, but more moving parts).
- Eviction policy - LRU vs LFU, and what happens on cold cache (deploy, restart, node failure) -> thundering herd risk again.

**Order to try in:**
1. read replicas
2. CDN for static assets
3.  app-layer cache (Redis/Memcached) with cache-aside
4.  denormalize hot paths
5.  address stampede/hot-key/invalidation as follow-ups when pushed

## Write Heavy Application
When you have an application receiving millions of writes how do you handle it without having to drop any events? Common examples include logging services

**Solutions:**
- Sharding writes across multiple nodes by key (hash based or range based)
- buffer and flush writes rather than doing one write per event
- Asynchronous writes with message queues and worker processes
- LSM-Tree databases such as Cassandra

**Order to try in:**
1. shard by key
2. durable message queue (Kafka, disk-persisted)
3. batch writes to storage 
4. LSM-tree DB for the write-optimized storage layer 
5. idempotent consumers for deduplication 
6. backpressure/autoscaling on consumer side when lag grows.
## Single point of failure

**Solutions:**
- Primary/Replicas
- failover if the primary fails

## Global Userbase
## Slow DB queries


**Order to Try in**
1. Optimize Queries
2. Create indexes, these slightly slow down writes while significantly improving reads
3. Sharding, using either range based or hash based distributions. Adds substantial complexity.
# References
- [[Cassandra DB]]
- 