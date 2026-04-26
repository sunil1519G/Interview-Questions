# Microservices Interview Questions (Intermediate)

Source PDF: `Microservices Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What is service discovery in microservices, and why is it needed?](#q-1)
- [2. How does the circuit breaker pattern improve resilience in microservices?](#q-2)
<a id="q-1"></a>
## 1. Question
What is service discovery in microservices, and why is it needed?

### Answer
Service discovery allows services to register and discover each other dynamically through a registry (for example Eureka/Consul), avoiding hardcoded addresses. This is crucial in microservices where instances scale up/down and IPs frequently change.

### Code Snippet
```java
@EnableDiscoveryClient // registers service with discovery server
@SpringBootApplication
public class OrderServiceApplication {
    public static void main(String[] args) {
        SpringApplication.run(OrderServiceApplication.class, args);
    }
}
```

### Keywords/Tags
- microservices
- intermediate
- service-discovery

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
How does the circuit breaker pattern improve resilience in microservices?

### Answer
Circuit breaker monitors downstream failures and opens the circuit when thresholds are exceeded, failing fast instead of repeatedly calling an unhealthy dependency. It prevents cascading failures and supports graceful fallback during outages.

### Code Snippet
```java
@CircuitBreaker(name = "inventory", fallbackMethod = "fallback") // protect remote dependency
public String checkStock(String sku) {
    return inventoryClient.check(sku); // call downstream service
}

public String fallback(String sku, Throwable ex) {
    return "stock-unknown"; // degraded-but-safe fallback response
}
```

### Keywords/Tags
- microservices
- intermediate
- circuit-breaker

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
