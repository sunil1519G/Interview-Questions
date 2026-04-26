# Design Patterns Interview Questions (Advanced)

Source PDF: `Design Patterns Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. How can you achieve thread-safe singleton patterns in Java?](#q-1)
- [2. What is an event-driven design pattern, and when should it be used?](#q-2)
<a id="q-1"></a>
## 1. Question
How can you achieve thread-safe singleton patterns in Java?

### Answer
For "How can you achieve thread-safe singleton patterns in Java?", state the pattern intent, participants, and the exact problem it solves. Add a concise Java-centric example and when not to apply the pattern to avoid unnecessary complexity.

### Code Snippet
```java
interface Shape { void draw(); } // abstraction

class Circle implements Shape {
    public void draw() { System.out.println("Drawing circle"); } // concrete behavior
}
```

### Keywords/Tags
- design-patterns
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What is an event-driven design pattern, and when should it be used?

### Answer
Event-driven pattern decouples event producers from consumers via event publishing/subscription. Producers emit events without knowing consumers; consumers register for events of interest. Use when: multiple components need to react to state changes asynchronously; loose coupling is critical (e.g., plugins, UI components, message queues). Avoid when: response time is critical (event dispatch adds latency) or complex event flow dependencies exist. Implement via Observer (simple, in-process) or Message Queue (distributed, resilient). Common in UI frameworks (button click events), real-time systems (stock price updates), and distributed systems (Kafka, RabbitMQ).

### Code Snippet
```java
import java.util.*;
import java.util.concurrent.*;

// 1. Simple Event-Driven Pattern: Observer
public interface EventListener<T> {
    void onEvent(Event<T> event);
}

public class Event<T> {
    private String type;
    private T data;
    private long timestamp;
    
    public Event(String type, T data) {
        this.type = type;
        this.data = data;
        this.timestamp = System.currentTimeMillis();
    }
    
    public String getType() { return type; }
    public T getData() { return data; }
    public long getTimestamp() { return timestamp; }
}

public class EventPublisher<T> {
    private List<EventListener<T>> listeners = new CopyOnWriteArrayList<>();
    
    public void subscribe(EventListener<T> listener) {
        listeners.add(listener);
    }
    
    public void unsubscribe(EventListener<T> listener) {
        listeners.remove(listener);
    }
    
    public void publish(Event<T> event) {
        // Notify all subscribed listeners asynchronously
        for (EventListener<T> listener : listeners) {
            new Thread(() -> listener.onEvent(event)).start();
        }
    }
}

// 2. Real-world Example: Stock Price Updates
public class StockPriceEvent {
    static class Stock {
        private String symbol;
        private double price;
        
        public Stock(String symbol, double price) {
            this.symbol = symbol;
            this.price = price;
        }
        
        public String getSymbol() { return symbol; }
        public double getPrice() { return price; }
    }
    
    // Event listener interface
    interface StockPriceListener {
        void onPriceUpdate(Stock stock, double oldPrice, double newPrice);
    }
    
    // Event publisher
    static class StockMarket {
        private Map<String, Double> prices = new ConcurrentHashMap<>();
        private Map<String, List<StockPriceListener>> listeners = new ConcurrentHashMap<>();
        
        public void subscribe(String symbol, StockPriceListener listener) {
            listeners.computeIfAbsent(symbol, k -> new CopyOnWriteArrayList<>())
                    .add(listener);
        }
        
        public void updatePrice(String symbol, double newPrice) {
            double oldPrice = prices.getOrDefault(symbol, 0.0);
            prices.put(symbol, newPrice);
            
            // Notify all listeners subscribed to this symbol
            if (listeners.containsKey(symbol)) {
                List<StockPriceListener> symbolListeners = listeners.get(symbol);
                for (StockPriceListener listener : symbolListeners) {
                    // Asynchronous notification
                    new Thread(() -> 
                        listener.onPriceUpdate(new Stock(symbol, newPrice), oldPrice, newPrice)
                    ).start();
                }
            }
        }
    }
    
    // Example implementation
    static class PortfolioTracker implements StockPriceListener {
        private Map<String, Double> portfolio;
        
        public PortfolioTracker(Map<String, Double> portfolio) {
            this.portfolio = portfolio;
        }
        
        @Override
        public void onPriceUpdate(Stock stock, double oldPrice, double newPrice) {
            if (portfolio.containsKey(stock.getSymbol())) {
                double quantity = portfolio.get(stock.getSymbol());
                double gainLoss = (newPrice - oldPrice) * quantity;
                System.out.println("Stock " + stock.getSymbol() + " updated: " + 
                    oldPrice + " -> " + newPrice + " (Impact: " + gainLoss + ")");
            }
        }
    }
}

// 3. Event Bus Pattern: centralized event routing
public class EventBus {
    private final ExecutorService executor = Executors.newFixedThreadPool(10);
    private Map<Class<?>, List<EventListener<?>>> listeners = new ConcurrentHashMap<>();
    
    public <T> void subscribe(Class<T> eventType, EventListener<T> listener) {
        listeners.computeIfAbsent(eventType, k -> new CopyOnWriteArrayList<>())
                .add(listener);
    }
    
    public <T> void publish(Event<T> event) {
        Class<?> eventType = event.getClass();
        if (listeners.containsKey(eventType)) {
            for (EventListener<?> listener : listeners.get(eventType)) {
                executor.submit(() -> ((EventListener<T>) listener).onEvent(event));
            }
        }
    }
}

// 4. Distributed Event-Driven: Queue-based (Kafka/RabbitMQ model)
public class AsyncEventQueue<T> {
    private final BlockingQueue<Event<T>> queue = new LinkedBlockingQueue<>();
    private final List<EventListener<T>> consumers = new CopyOnWriteArrayList<>();
    private volatile boolean running = true;
    
    public AsyncEventQueue() {
        // Start consumer thread
        new Thread(() -> {
            while (running) {
                try {
                    Event<T> event = queue.poll(100, TimeUnit.MILLISECONDS);
                    if (event != null) {
                        for (EventListener<T> consumer : consumers) {
                            consumer.onEvent(event); // process event
                        }
                    }
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                }
            }
        }).start();
    }
    
    public void subscribe(EventListener<T> listener) {
        consumers.add(listener);
    }
    
    public void publish(Event<T> event) {
        try {
            queue.put(event); // non-blocking from publisher's perspective
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
    
    public void stop() {
        running = false;
    }
}
```

### Keywords/Tags
- design-patterns
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
