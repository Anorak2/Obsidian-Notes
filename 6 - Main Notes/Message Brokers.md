
2026-08-09

Tags: [[Designing Data Intensive Applications]]
# Message Brokers
The simplest way for two different services to communicate is with a direct call, such as an HTTP request. This works well up until the other service is slow or unavailable which causes problems. Since this is a very common problem a message broker creates a queue capable of holding onto these requests. This allows the downstream service to handle them as fast as it can and no requests are lost.

## Kafka
Kafka is essential a distributed append only log, it doesn't go away after being read by a consumer; only deleted at the end of a retention period. The Consumers are responsible for tracking which part of the queue they have been able to work through, called an offset. On a crash a consumer can reload this offset, and if a request from the past is necessary the offset can just be changed.

Kafka is a fundamentally simple broker that requires smart consumers, the consumers choose what to read and when. This allows for durable and replayable messages, and multiple different services can read from the same topic at once. A new service can even read from the entire backfill at once in order to propagate data, only made possible through the log. 

**Trade Offs**
Kafka can handle one million plus messages a second, with 5-50 MS of latency. It is known for being harder to run, since like memcached Kafka itself is simpler. This typically means `ZooKeeper`, partition management, and more moving parts. The complexities can be handled by a managed service such as `Confluence Cloud`, `Amazon MSK`, or `Azure Event Hubs`. 

## RabbitMQ
This broker has a simple system where a producer sends a message to a broker, the broker routes it based off some set of rules, and a consumer can pull a message off the queue. After acknowledging the message RabbitMQ deletes the message from the queue. This approach allows for message routing, retrying on failure, delivery tracking, and after multiple failures a message is sent to a "dead letter" queue for debugging.

RabbitMQ is a smart broker that performs a large amount of work, allowing for simple consumers. This model works well for task oriented patterns such as processing transactions, emails, or any other unit of work. 

**Trade Offs**
RabbitMQ can handle about 4,000-10,000 messages a second and 1-5 MS latency. It has a single binary and simpler clustering than Kafka, it even has a management UI.

# References
- [[Memcached]]