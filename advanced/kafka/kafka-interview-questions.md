# Kafka Interview Questions (Advanced)

Source PDF: `Kafka Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What do you mean by a Partition in Kafka?](#q-1)
- [2. What is the purpose of partitions in Kafka?](#q-2)
- [3. Can the number of partitions for a topic be changed in Kafka?](#q-3)
<a id="q-1"></a>
## 1. Question
What do you mean by a Partition in Kafka?

### Answer
For "What do you mean by a Partition in Kafka?", explain producer/topic/partition/consumer-group mechanics and how delivery guarantees are achieved. Mention ordering, rebalancing, and idempotency implications.

### Code Snippet
```java
@KafkaListener(topics = "orders", groupId = "billing") // consumer subscription
public void consume(String event) {
    // Parse and process order event safely
}
```

### Keywords/Tags
- kafka
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What is the purpose of partitions in Kafka?

### Answer
For "What is the purpose of partitions in Kafka?", explain producer/topic/partition/consumer-group mechanics and how delivery guarantees are achieved. Mention ordering, rebalancing, and idempotency implications.

### Code Snippet
```java
@KafkaListener(topics = "orders", groupId = "billing") // consumer subscription
public void consume(String event) {
    // Parse and process order event safely
}
```

### Keywords/Tags
- kafka
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
Can the number of partitions for a topic be changed in Kafka?

### Answer
For "Can the number of partitions for a topic be changed in Kafka?", explain producer/topic/partition/consumer-group mechanics and how delivery guarantees are achieved. Mention ordering, rebalancing, and idempotency implications.

### Code Snippet
```java
@KafkaListener(topics = "orders", groupId = "billing") // consumer subscription
public void consume(String event) {
    // Parse and process order event safely
}
```

### Keywords/Tags
- kafka
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
