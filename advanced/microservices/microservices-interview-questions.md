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
Distributed tracing tracks requests across service boundaries using unique trace IDs (same for entire request flow) and span IDs (per service). It reveals: latency breakdown per service, dependency chains, failure points, and bottlenecks. Without tracing, debugging is impossible: logs are scattered, service interactions hidden. Tracing tools (Jaeger, Zipkin, DataDog) correlate logs, metrics, and traces. Essential for SLA compliance: identify slow services, optimize hot paths, understand cascading failures. Context propagation (HTTP headers, message metadata) maintains trace continuity across async boundaries.

### Code Snippet
```java
import io.opentelemetry.api.trace.Tracer;
import io.opentelemetry.api.trace.Span;
import io.opentelemetry.context.Context;
import org.springframework.cloud.sleuth.Tracer;
import org.springframework.http.HttpHeaders;

// 1. Manual distributed tracing with OpenTelemetry
public class DistributedTracingExample {
    
    private static Tracer tracer; // OpenTelemetry tracer
    
    // Service A: receives request with trace ID in header
    public void serviceA(HttpServletRequest request) {
        // Extract trace ID from request header (X-Trace-ID)
        String traceId = request.getHeader("X-Trace-ID");
        if (traceId == null) {
            traceId = UUID.randomUUID().toString(); // create new trace
        }
        
        // Create span for this service's work
        try (Span span = tracer.spanBuilder("serviceA")
                .setAttribute("trace.id", traceId)
                .startSpan()) {
            
            span.addEvent("Processing order");
            
            // Call Service B: propagate trace ID
            callServiceB(traceId);
            
            span.addEvent("Order processing complete");
        }
    }
    
    // Service B: receives trace ID and continues tracing
    private void callServiceB(String traceId) {
        // Create HTTP request with trace ID
        HttpClient client = HttpClient.newHttpClient();
        HttpRequest request = HttpRequest.newBuilder()
                .uri(URI.create("http://serviceB:8081/process"))
                .header("X-Trace-ID", traceId) // propagate trace
                .header("X-Span-ID", UUID.randomUUID().toString()) // new span
                .build();
        
        try (Span span = tracer.spanBuilder("callServiceB")
                .setAttribute("trace.id", traceId)
                .setAttribute("span.parent", "serviceA")
                .startSpan()) {
            
            span.addEvent("Sending request to Service B");
            HttpResponse<String> response = client.send(request, HttpResponse.BodyHandlers.ofString());
            
            span.addEvent("Received response: " + response.statusCode());
            span.setAttribute("http.status", response.statusCode());
        }
    }
}

// 2. Spring Cloud Sleuth: automatic tracing
@RestController
public class OrderServiceWithSleuth {
    
    private Tracer tracer; // Spring Cloud Sleuth
    private RestTemplate restTemplate;
    
    @PostMapping("/orders")
    public ResponseEntity<?> createOrder(@RequestBody OrderRequest request) {
        // Sleuth automatically creates trace span
        // Trace ID visible in logs
        
        logger.info("Creating order"); // [order-service,a1b2c3d4e5f6g7h8,00000000000000a1]
        // Format: [app-name, trace-id, span-id]
        
        try (Span span = tracer.nextSpan().name("createOrder").start()) {
            span.tag("order.id", request.getOrderId());
            span.tag("order.amount", request.getAmount());
            
            // Call Payment Service
            PaymentResponse payment = restTemplate.postForObject(
                "http://payment-service/charge",
                new PaymentRequest(request.getAmount()),
                PaymentResponse.class
            );
            // Sleuth automatically adds trace headers to HTTP request
            
            // Call Inventory Service
            InventoryResponse inventory = restTemplate.postForObject(
                "http://inventory-service/reserve",
                new InventoryRequest(request.getItems()),
                InventoryResponse.class
            );
            
            logger.info("Order created successfully");
            return ResponseEntity.ok(new OrderResponse(request.getOrderId(), "SUCCESS"));
        }
    }
}

// 3. Distributed tracing flow
public class DistributedTracingFlow {
    /*
     * CLIENT REQUEST:
     * GET /api/orders/123
     * [no trace context]
     * 
     * API GATEWAY (generates trace):
     * Trace-ID: abc123
     * Span-ID: span001
     * 
     * SERVICE A (receives trace context):
     * Trace-ID: abc123 (same)
     * Span-ID: span002 (new span)
     * Parent-Span-ID: span001
     * [log] Processing order in ServiceA
     * 
     * SERVICE A calls SERVICE B:
     * HTTP Header: X-Trace-ID: abc123
     * HTTP Header: X-Span-ID: span002
     * 
     * SERVICE B (receives trace context):
     * Trace-ID: abc123 (same)
     * Span-ID: span003 (new span)
     * Parent-Span-ID: span002
     * [log] Validating inventory in ServiceB
     * 
     * SERVICE B calls SERVICE C:
     * HTTP Header: X-Trace-ID: abc123
     * HTTP Header: X-Span-ID: span003
     * 
     * SERVICE C (receives trace context):
     * Trace-ID: abc123 (same)
     * Span-ID: span004 (new span)
     * Parent-Span-ID: span003
     * [log] Checking database in ServiceC
     * 
     * TRACE TREE (Jaeger/Zipkin visualizes):
     *
     * span001 (API Gateway) - 100ms
     * └─ span002 (ServiceA) - 80ms
     *    └─ span003 (ServiceB) - 60ms
     *       └─ span004 (ServiceC) - 50ms [DATABASE CALL 45ms]
     * 
     * INSIGHTS:
     * - Total latency: 100ms
     * - ServiceC database call: 45ms (bottleneck)
     * - Network latency between services: ~5ms per hop
     * - Serialization/deserialization: ~5ms total
     * 
     * OPTIMIZATION OPPORTUNITY:
     * - Add database connection pool
     * - Cache frequently accessed data
     * - Parallelize independent service calls
     */
}

// 4. Practical debugging with traces
public class DebuggingWithTraces {
    
    public static void findSlowRequest() {
        /*
         * Scenario: Order API takes 5 seconds sometimes, 500ms other times
         * 
         * WITHOUT TRACING:
         * - Check logs: scattered across multiple services
         * - No correlation between service logs
         * - Unknown which service is slow
         * - Impossible to debug
         * 
         * WITH TRACING (Jaeger UI):
         * 1. Query by service: "orderService"
         * 2. Filter by latency: > 3000ms
         * 3. View trace timeline:
         *    - OrderService: 100ms
         *    - PaymentService: 2500ms (SLOW!)
         *    - InventoryService: 1200ms
         *    - NotificationService: 200ms
         * 4. Drill into PaymentService span:
         *    - External API call: 2400ms (timeout?)
         *    - Retry attempt: 1500ms (second attempt)
         *    - Third attempt succeeded: 100ms
         * 5. Root cause: PaymentService external API is flaky
         * 6. Solution: implement circuit breaker, add fallback
         */
    }
    
    public static void findCascadingFailure() {
        /*
         * Scenario: OrderService times out when InventoryService fails
         * 
         * TRACE SHOWS:
         * OrderService calls InventoryService (no timeout)
         * InventoryService calls DatabaseService (hangs)
         * DatabaseService connection pool exhausted
         * OrderService waits indefinitely
         * 
         * FIX:
         * - Add timeout to InventoryService call
         * - Add connection pool limits to DatabaseService
         * - Use circuit breaker to fail fast
         * - Add health checks
         */
    }
}

// 5. Context propagation for async workloads
public class ContextPropagationAsync {
    
    public void processOrderAsync(String orderId, String traceId) {
        // When publishing to message queue (Kafka, RabbitMQ)
        Message message = new Message();
        message.setOrderId(orderId);
        message.setHeader("X-Trace-ID", traceId); // propagate trace
        message.setHeader("X-Span-ID", UUID.randomUUID().toString());
        
        kafkaTemplate.send("orders-topic", message);
    }
    
    @KafkaListener(topics = "orders-topic")
    public void handleOrderAsync(Message message) {
        // Extract trace context from message header
        String traceId = message.getHeader("X-Trace-ID");
        
        try (Span span = tracer.nextSpan().name("handleOrderAsync")
                .tag("trace.id", traceId).start()) {
            
            // Process order; span is linked to original request trace
            processOrder(message.getOrderId());
        }
    }
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
