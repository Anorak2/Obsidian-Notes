
2026-07-12

Tags: [[Performance Measurement & Reliability]] [[Designing Data Intensive Applications]]
# What is Scalability
Load can be described with a few numbers which we call load parameters. The best choice of parameters depends on the architecture of your system. Perhaps it’s requests per second to a webserver, ratio of reads to writes in a database, the number of simultaneously active users in a chat room, the hit rate on a cache, or something else. Perhaps the average case is what matters for you, or perhaps your bottleneck is dominated by a small number of extreme cases.

**describing performance requirements**
- When you increase a load parameter, and keep the system resources (CPU, memory, network bandwidth, etc.) unchanged, how is performance of your sys‐ tem affected?
- When you increase a load parameter, how much do you need to increase the resources if you want to keep performance unchanged?

## Describing Performance (Metrics)

| Metric        |                                                                                                               |
| ------------- | ------------------------------------------------------------------------------------------------------------- |
| Throughput    | The number of records that can be processed per second, or the total runtime required for a certain operation |
| Response-Time | The time between a client sending a request and receiving a response                                          |
| Latency       | the amount of time a request spends waiting to be handled, or is latent.                                      |

For business purposes it is usually most useful to talk about percentiles, especially percentiles at the tails. For example we may be interested in `p99`, which is the threshold at which 99% of the responses are faster. High percentiles are important since as an example if we optimize for say `p50`, the median, we may be losing out on the customers that represent the slowest 10% of times. As a result of the value placed on the tails Amazon works at `p999`. 

## Scaling
There is no such thing as a magic bullet for scalability, and labeling a system as "scaling" or "not-scaling" is meaningless since scalability is a spectrum. Likewise based on the usecase it can be better to pick a solution that scales "worse" but performs better within certain parameters. If you choose this approach it is often smart to place an assertion so that if your assumption on the input ever changes you can go back and refactor it based on the new parameters.
# References
- 