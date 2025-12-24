
https://logit.io/blog/post/performance-profiling-optimization-enterprise-guide/
## Things I need to finish
- [x] Scientific Method
- [x] Finish Data Mining LLM slides
- [ ] Test Driven Development
- [ ] SDLC
- [ ] LAN's
- [ ] GIT - 6h total
	- [ ] 2h
	- [ ] 2h
- [ ] Data Transfer Objects
- [x] Semaphores
- [x] Review 645 slides 10-15
- [x] Architecture
- [ ] Review OS
## Performance Measurement & Profiling
- [x] Performance measurement methodology
- [x] Benchmark design
- [x] Profiling
- [ ] Profiling at scale
- [ ] Cache-aware / cache-oblivious thinking
- [ ] Memory allocation behavior
- [ ] NUMA effects
- [ ] False sharing
- [ ] Tail latency analysis (p99, p999)
- [ ] Throughput vs latency tradeoffs
- [ ] Backpressure modeling
- [ ] I/O monitoring
- [ ] Thread and Concurrency profiling; including thread contention, deadlock detection, and synchronization overhead that enable effective concurrency optimization and parallelism improvement. Concurrency profiling includes contention analysis, deadlock detection, and synchronization optimization that support multi-threaded performance improvement and parallelism efficiency.
- [ ] Real-time profiling and monitoring provide continuous performance visibility through live profiling data, real-time analysis, and immediate feedback that enable proactive performance management and rapid optimization response. Real-time profiling includes live monitoring, immediate analysis, and responsive optimization that support proactive performance management and rapid issue resolution
- [ ] Database Query Optimization
- [ ] 

## CPU & Low-Level Performance
- [x] CPU performance counters (perf, VTune concepts)
- [x] Flame graphs
- [x] Microbenchmark pitfalls
- [ ] Memory allocators (ptmalloc, jemalloc, tcmalloc)
- [ ] NUMA architecture
- [ ] Latency distributions (not just averages)

## Review Concurrency Fundamentals
- [ ] Locks
- [ ] Scheduling
- [ ] Peterson’s algorithm
- [ ] Synchronization theory

## Modern Production Concurrency Patterns
- [ ] Lock-free data structures (beyond theory)
- [ ] Memory models (C11 / Go memory model)
- [ ] Happens-before reasoning in real code
- [ ] ABA problem
- [ ] Atomic primitives in practice
- [ ] Work stealing in real runtimes
- [ ] Structured concurrency
- [ ] Async vs threads tradeoffs

## Networking, OS & Database Systems
- [ ] Rate limiting algorithms
- [ ] Load shedding
- [ ] Circuit breakers
- [ ] Backpressure propagation
- [ ] Consistent hashing (practical variants)
- [ ] Sharding rebalancing strategies
- [ ] Hot-key mitigation
- [ ] Service degradation strategies
- [ ] Idempotency guarantees

## Databases & Storage Internals
- [ ] Log-structured storage
- [ ] WAL design
- [ ] B-tree vs LSM tradeoffs
- [ ] Page layouts
- [ ] Cache eviction strategies
- [ ] Compression techniques
- [ ] Write amplification
- [ ] Checkpointing in practice

## Engineering-Side Optimization
- [ ] Vectorization (SIMD)
- [ ] Branch prediction effects
- [ ] Data-oriented design
- [ ] Memory layout transformations
- [ ] Cache line alignment
- [ ] Bit-level tricks (systematic)
- [ ] SIMD in C (AVX basics)
- [ ] Structure-of-arrays vs array-of-structures
- [ ] Prefetching
- [ ] Loop transformations

## Security & Operational Reliability
- [ ] Graceful degradation
- [ ] Partial failure handling
- [ ] Chaos testing concepts
- [ ] Observability (metrics, tracing, logs as signals)
- [ ] Post-mortem culture
