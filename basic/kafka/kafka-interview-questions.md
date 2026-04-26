# Kafka Interview Questions (Basic)

Source PDF: `Kafka Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What does it mean if a replica is not an In-Sync Replica for a long time?](#q-1)
<a id="q-1"></a>
## 1. Question
What does it mean if a replica is not an In-Sync Replica for a long time?

### Answer
For "What does it mean if a replica is not an In-Sync Replica for a long time?", explain producer/topic/partition/consumer-group mechanics and how delivery guarantees are achieved. Mention ordering, rebalancing, and idempotency implications.

### Code Snippet
```java
@KafkaListener(topics = "orders", groupId = "billing") // consumer subscription
public void consume(String event) {
    // Parse and process order event safely
}
```

### Keywords/Tags
- kafka
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
