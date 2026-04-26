# Microservices Interview Questions (Basic)

Source PDF: `Microservices Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What are the benefits and drawbacks of Microservices?](#q-1)
- [2. What is the role of actuator in spring boot?](#q-2)
- [3. What issues are generally solved by spring clouds?](#q-3)
- [4. What do you mean by Cohesion and Coupling?](#q-4)
- [5. What do you mean by Bounded Context?](#q-5)
- [6. What are the challenges that one has to face while using Microservices?](#q-6)
- [7. What do you mean by client certificates?](#q-7)
- [8. What do you mean by Semantic Monitoring?](#q-8)
- [9. What do you mean by Domain driven design?](#q-9)
- [10. What do you mean by end-to-end microservices testing?](#q-10)
- [11. What are Reactive Extensions in Microservices?](#q-11)
- [12. What do you mean by Mike Cohn’s Test Pyramid?](#q-12)
- [13. What is the main role of docker in microservices?](#q-13)
<a id="q-1"></a>
## 1. Question
What are the benefits and drawbacks of Microservices?

### Answer
For "What are the benefits and drawbacks of Microservices?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What is the role of actuator in spring boot?

### Answer
Spring Boot Actuator provides production-ready monitoring endpoints such as `/health`, `/metrics`, and `/info`. It improves observability, but sensitive endpoints should be secured and exposed selectively.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
What issues are generally solved by spring clouds?

### Answer
For "What issues are generally solved by spring clouds?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
What do you mean by Cohesion and Coupling?

### Answer
For "What do you mean by Cohesion and Coupling?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
What do you mean by Bounded Context?

### Answer
For "What do you mean by Bounded Context?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
What are the challenges that one has to face while using Microservices?

### Answer
For "What are the challenges that one has to face while using Microservices?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-7"></a>
## 7. Question
What do you mean by client certificates?

### Answer
For "What do you mean by client certificates?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-8"></a>
## 8. Question
What do you mean by Semantic Monitoring?

### Answer
For "What do you mean by Semantic Monitoring?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-9"></a>
## 9. Question
What do you mean by Domain driven design?

### Answer
For "What do you mean by Domain driven design?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-10"></a>
## 10. Question
What do you mean by end-to-end microservices testing?

### Answer
For "What do you mean by end-to-end microservices testing?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-11"></a>
## 11. Question
What are Reactive Extensions in Microservices?

### Answer
For "What are Reactive Extensions in Microservices?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-12"></a>
## 12. Question
What do you mean by Mike Cohn’s Test Pyramid?

### Answer
For "What do you mean by Mike Cohn’s Test Pyramid?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-13"></a>
## 13. Question
What is the main role of docker in microservices?

### Answer
For "What is the main role of docker in microservices?", describe request flow between services and the reliability controls involved (timeouts, retries, circuit breakers, idempotency, and tracing). Call out one failure mode and mitigation strategy.

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
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
