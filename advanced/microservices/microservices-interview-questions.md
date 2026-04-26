# Microservices Interview Questions (Advanced)

Source PDF: `Microservices Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What do you mean by Distributed Transaction?](#q-1)
- [2. Why is distributed tracing important in microservices?](#q-2)
<a id="q-1"></a>
## 1. Question
What do you mean by Distributed Transaction?

### Answer
For "What do you mean by Distributed Transaction?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

### Code Snippet
```java
@CircuitBreaker(name = "inventory", fallbackMethod = "fallback") // resilience guard
public String checkStock(String sku) {
    return inventoryClient.check(sku); // external service call
}

public String fallback(String sku, Throwable ex) {
    return "stock-unknown"; // graceful degradation response
}
```

### Keywords/Tags
- microservices
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
Why is distributed tracing important in microservices?

### Answer
Distributed tracing tracks requests across service boundaries using trace and span IDs. It helps diagnose latency, failure hotspots, and dependency bottlenecks in distributed systems.

### Code Snippet
```java
@CircuitBreaker(name = "inventory", fallbackMethod = "fallback") // resilience guard
public String checkStock(String sku) {
    return inventoryClient.check(sku); // external service call
}

public String fallback(String sku, Throwable ex) {
    return "stock-unknown"; // graceful degradation response
}
```

### Keywords/Tags
- microservices
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
