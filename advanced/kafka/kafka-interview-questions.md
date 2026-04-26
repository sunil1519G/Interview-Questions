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
You can INCREASE partitions but CANNOT DECREASE them. When you add partitions, Kafka reallocates data across brokers. However, existing messages remain in original partitions; only new messages are distributed to new partitions. This can break ordering guarantees if you depend on partition count being fixed (e.g., partition key assumptions). Producers should use custom partition assignments to handle partition count changes gracefully. Plan partition count carefully at topic creation; increasing partitions requires broker rebalancing and causes brief latency spikes. Consumer group rebalancing happens automatically when partition count changes.

### Code Snippet
```java
import org.apache.kafka.clients.admin.*;
import java.util.*;
import java.util.concurrent.ExecutionException;

public class PartitionModification {
    
    // Cannot decrease partitions: design-time decision
    public static void partitionIncrease() throws ExecutionException, InterruptedException {
        AdminClient admin = AdminClient.create(Map.of(
            AdminClientConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092"
        ));
        
        // Create topic with 3 partitions
        NewTopic topic = new NewTopic("orders", 3, (short) 1);
        admin.createTopics(Collections.singleton(topic)).all().get();
        System.out.println("Topic created with 3 partitions");
        
        // Producer sends messages to 3 partitions
        // Partition: 0 has msg1, msg4, msg7
        // Partition: 1 has msg2, msg5, msg8
        // Partition: 2 has msg3, msg6, msg9
        
        // LATER: Increase to 6 partitions
        Map<String, NewPartitions> newPartitions = new HashMap<>();
        newPartitions.put("orders", NewPartitions.increaseTo(6));
        
        admin.createPartitions(newPartitions).all().get();
        System.out.println("Topic partitions increased to 6");
        
        // Old data remains in original partitions (0-2)
        // New messages go to all 6 partitions
        // Partition layout becomes:
        // [0: msg1, msg4, msg7]
        // [1: msg2, msg5, msg8]
        // [2: msg3, msg6, msg9]
        // [3: msg10, ...]
        // [4: msg11, ...]
        // [5: msg12, ...]
        
        admin.close();
    }
    
    // Cannot decrease: this is NOT supported
    public static void partitionDecrease() {
        /*
         * KAFKA DOES NOT SUPPORT PARTITION DECREASE
         * 
         * Why?
         * 1. Data loss: where to move messages from deleted partitions?
         * 2. Ordering guarantees: existing code assumes partition count
         * 3. Consumer offset tracking: consumer.offset tied to partition
         * 
         * To reduce partitions: delete and recreate topic (data loss!)
         */
        System.out.println("Decreasing partitions is not supported by Kafka");
        System.out.println("Workaround: delete topic and recreate with fewer partitions");
        System.out.println("This DELETES all messages in the topic");
    }
    
    // Impact on partition key hashing
    public static void partitionKeyImpact() {
        /*
         * Partition assignment formula: partition = key_hash % num_partitions
         * 
         * Scenario 1: Initial setup
         * Topic: "orders", Partitions: 3
         * Key: "customer_123"
         * Hash: 42
         * Assigned partition: 42 % 3 = 0
         * 
         * Scenario 2: After increasing to 6 partitions
         * Key: "customer_123"
         * Hash: 42
         * Assigned partition: 42 % 6 = 0 (SAME partition)
         * 
         * BUT for other keys:
         * Key: "customer_456"
         * Hash: 77
         * OLD: 77 % 3 = 2
         * NEW: 77 % 6 = 5 (DIFFERENT partition!)
         * 
         * Implication: ORDERING BREAK for customer_456
         * Old messages in partition 2, new messages in partition 5
         * Consumer group rebalancing happens: brief window of disorder
         */
        System.out.println("Partition key distribution changes when partition count increases");
        System.out.println("For most keys, partition assignment changes");
        System.out.println("This can break ordering guarantees temporarily during rebalancing");
    }
    
    // Best practices
    public static void bestPractices() {
        System.out.println("=== Partition Best Practices ===");
        System.out.println("1. Plan partition count at topic creation");
        System.out.println("2. Use rule of thumb: 1 partition per 10-15 MB/sec throughput");
        System.out.println("3. Start with more partitions than needed (scale down is not possible)");
        System.out.println("4. Increasing partitions: acceptable, causes brief rebalancing");
        System.out.println("5. Partition increase doesn't retroactively fix key distribution");
        System.out.println("6. Consumer groups auto-rebalance when partitions change");
        System.out.println("7. Use custom partitioner if default behavior doesn't suit (rare)");
    }
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
