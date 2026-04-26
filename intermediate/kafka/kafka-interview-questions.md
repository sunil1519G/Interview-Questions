# Kafka Interview Questions (Intermediate)

Source PDF: `Kafka Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What are some of the features of Kafka?](#q-1)
- [2. What are the major components of Kafka?](#q-2)
- [3. What do you mean by zookeeper in Kafka and what are its uses?](#q-3)
- [4. Can we use Kafka without Zookeeper?](#q-4)
- [5. Why is Topic Replication important in Kafka? What do you mean by ISR in Kafka?](#q-5)
- [6. What do you understand about a consumer group in Kafka?](#q-6)
- [7. What is the maximum size of a message that Kafka can receive?](#q-7)
- [8. How do you start a Kafka server?](#q-8)
- [9. What do you mean by geo-replication in Kafka?](#q-9)
- [10. What are some of the disadvantages of Kafka?](#q-10)
- [11. What are the use cases of Kafka monitoring?](#q-11)
- [12. What do you mean by Kafka schema registry?](#q-12)
- [13. What are the benefits of using clusters in Kafka?](#q-13)
- [14. What do you mean by multi-tenancy in Kafka?](#q-14)
- [15. What do you understand about Kafka MirrorMaker?](#q-15)
- [16. What do you mean by confluent kafka? What are its advantages?](#q-16)
- [17. What do you understand about log compaction and quotas in Kafka?](#q-17)
- [18. What are the guarantees that Kafka provides?](#q-18)
- [19. What do you mean by an unbalanced cluster in Kafka? How can you balance it?](#q-19)
- [20. How will you expand a cluster in Kafka?](#q-20)
- [21. What do you mean by graceful shutdown in Kafka?](#q-21)
- [22. How will you change the retention time in Kafka at runtime?](#q-22)
- [23. What are Znodes in Kafka Zookeeper? How many types of Znodes are there?](#q-23)
<a id="q-1"></a>
## 1. Question
What are some of the features of Kafka?

### Answer
Kafka provides high-throughput append-only logs, horizontal scalability via partitions, fault tolerance via replication, durable storage, and consumer replay by offsets. It also supports stream processing and event-driven architectures with strong ordering guarantees per partition.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What are the major components of Kafka?

### Answer
Core Kafka components are Producers, Brokers, Topics, Partitions, Consumers, Consumer Groups, and (depending on mode) ZooKeeper/KRaft controller quorum. Together they manage ingestion, storage, replication, and consumption coordination.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
What do you mean by zookeeper in Kafka and what are its uses?

### Answer
In ZooKeeper-based Kafka clusters, ZooKeeper stores metadata such as broker registration and controller election state. Newer Kafka deployments can run in KRaft mode, reducing dependence on ZooKeeper.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
Can we use Kafka without Zookeeper?

### Answer
Yes. Modern Kafka supports KRaft (Kafka Raft metadata mode), where brokers manage metadata quorum internally without ZooKeeper. This is now the preferred long-term architecture.

### Code Snippet
```properties
# KRaft mode: metadata handled by Kafka itself (no ZooKeeper)
process.roles=broker,controller
controller.quorum.voters=1@localhost:9093
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
Why is Topic Replication important in Kafka? What do you mean by ISR in Kafka?

### Answer
Replication protects data against broker failure by maintaining leader/follower replicas per partition. ISR (In-Sync Replicas) is the replica set sufficiently caught up with leader; producer acks and min.insync.replicas rely on ISR for durability.

### Code Snippet
```properties
# Durability-focused producer settings
acks=all                    # wait for ISR acknowledgement
min.insync.replicas=2       # require at least two in-sync replicas
enable.idempotence=true     # avoid duplicate retries at producer side
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
What do you understand about a consumer group in Kafka?

### Answer
A consumer group is a set of consumers sharing the same group id so partitions are distributed among them for parallelism. Within one group, each partition is consumed by at most one active consumer at a time.

### Code Snippet
```java
@KafkaListener(topics = "orders", groupId = "billing") // one group member handles each partition
public void consume(String event) {
    // process event and commit offset through listener container policy
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-7"></a>
## 7. Question
What is the maximum size of a message that Kafka can receive?

### Answer
Kafka message size is configurable; default broker limit is typically around 1 MB (`message.max.bytes`). Larger payloads require coordinated producer/broker/consumer settings, but very large messages are generally discouraged.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-8"></a>
## 8. Question
How do you start a Kafka server?

### Answer
Start Kafka by launching the broker process with a server config (`server.properties`). In local setups, start metadata service (ZooKeeper or KRaft controller quorum) first, then start brokers and verify logs/port health.

### Code Snippet
```bash
# Start Kafka broker with server configuration
kafka-server-start.sh config/server.properties
# Check logs for listener startup and controller registration
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-9"></a>
## 9. Question
What do you mean by geo-replication in Kafka?

### Answer
Geo-replication copies topics across regions/data centers for disaster recovery and locality. Tools like MirrorMaker 2 replicate selected topics, offsets, and ACL metadata depending on policy.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-10"></a>
## 10. Question
What are some of the disadvantages of Kafka?

### Answer
Kafka adds operational complexity: partition planning, retention tuning, rebalancing behavior, and monitoring overhead. It is excellent for event streams but may be overkill for low-volume, simple request-response workloads.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-11"></a>
## 11. Question
What are the use cases of Kafka monitoring?

### Answer
Kafka monitoring is used to detect lag, under-replicated partitions, broker pressure, ISR shrink events, and throughput anomalies. It supports SLA protection, capacity planning, and incident response.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-12"></a>
## 12. Question
What do you mean by Kafka schema registry?

### Answer
Schema Registry stores and versions event schemas (Avro/Protobuf/JSON Schema) and enforces compatibility rules. It prevents producer-consumer contract breakage during schema evolution.

### Code Snippet
```properties
# Producer uses Confluent Schema Registry for Avro serialization
spring.kafka.properties.schema.registry.url=http://localhost:8081
spring.kafka.producer.value-serializer=io.confluent.kafka.serializers.KafkaAvroSerializer
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-13"></a>
## 13. Question
What are the benefits of using clusters in Kafka?

### Answer
Kafka clusters provide scalability, fault tolerance, and workload distribution. Multiple brokers allow high throughput and resilience, while partition leadership spread prevents single-node bottlenecks.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-14"></a>
## 14. Question
What do you mean by multi-tenancy in Kafka?

### Answer
Multi-tenancy in Kafka means sharing a cluster among teams/apps safely using topic naming conventions, ACLs, quotas, and resource isolation policies to avoid noisy-neighbor impact.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-15"></a>
## 15. Question
What do you understand about Kafka MirrorMaker?

### Answer
MirrorMaker (especially MM2) replicates topics across Kafka clusters for DR, migration, and regional data distribution. It supports offset sync and selective topic replication strategies.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-16"></a>
## 16. Question
What do you mean by confluent kafka? What are its advantages?

### Answer
Confluent Platform is a Kafka ecosystem distribution with enterprise tooling (Schema Registry, Connectors, ksqlDB, Control Center, RBAC/security features). It accelerates production operations and governance.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-17"></a>
## 17. Question
What do you understand about log compaction and quotas in Kafka?

### Answer
Log compaction retains the latest record per key, useful for changelog/state topics. Quotas throttle producer/consumer or client traffic to protect cluster stability and fairness.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-18"></a>
## 18. Question
What are the guarantees that Kafka provides?

### Answer
Kafka guarantees ordering within a partition, durability based on replication/acks, and at-least-once delivery by default. With idempotent producers and transactions, exactly-once semantics can be achieved in specific pipelines.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-19"></a>
## 19. Question
What do you mean by an unbalanced cluster in Kafka? How can you balance it?

### Answer
An unbalanced cluster has uneven partition leadership or data distribution causing hotspot brokers. Rebalance via partition reassignment, leader election optimization, and capacity-aware partition strategy.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-20"></a>
## 20. Question
How will you expand a cluster in Kafka?

### Answer
To expand a Kafka cluster, add brokers, update configs/advertised listeners, and reassign partitions so data and traffic spread across new nodes. Expansion should be done with monitoring to avoid ISR or lag regressions.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-21"></a>
## 21. Question
What do you mean by graceful shutdown in Kafka?

### Answer
Graceful shutdown lets brokers/consumers stop without abrupt data or coordination issues. Consumers should commit offsets and close cleanly; brokers stop accepting new traffic and hand off leadership safely.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-22"></a>
## 22. Question
How will you change the retention time in Kafka at runtime?

### Answer
Retention can be changed at runtime using topic-level configs (for example `retention.ms`) via admin tools/APIs. Kafka applies the new policy without restarting brokers.

### Code Snippet
```bash
# Change topic retention to 24 hours without broker restart
kafka-configs.sh --bootstrap-server localhost:9092   --entity-type topics --entity-name orders   --alter --add-config retention.ms=86400000
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-23"></a>
## 23. Question
What are Znodes in Kafka Zookeeper? How many types of Znodes are there?

### Answer
In ZooKeeper mode, znodes are metadata nodes used for broker/controller and other coordination data. Znode types are persistent, ephemeral, persistent-sequential, and ephemeral-sequential.

### Code Snippet
```java
// Kafka consumer example with comments
@KafkaListener(topics = "orders", groupId = "analytics")
public void onMessage(String payload) {
    // parse payload
    // apply business logic
}
```

### Keywords/Tags
- kafka
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
