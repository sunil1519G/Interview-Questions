# Java Collections Interview Questions (Intermediate)

Source PDF: `Java Collections Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What is the difference between Array and Collection in java?](#q-1)
<a id="q-1"></a>
## 1. Question
What is the difference between Array and Collection in java?

### Answer
Arrays have fixed size (determined at creation), provide O(1) index-based access, and are stack-allocated for primitives. Collections (List/Set/Map) have dynamic size, support variable performance, are heap-allocated, and offer thread-safe variants. Arrays are best for known fixed-size data; Collections are best for dynamic, variable-size data with type safety.

### Code Snippet
```java
import java.util.*;
import java.util.concurrent.ConcurrentHashMap;

public class ArraysVsCollections {
    
    public void arrayExample() {
        int[] numbers = new int[5]; // fixed size = 5
        numbers[0] = 10; // O(1) index access
        // numbers[5] = 30; // RUNTIME ERROR
        
        String[] names = {"Alice", "Bob", "Charlie"}; // fixed size
        System.out.println(names[0]); // O(1) access
        // no built-in methods like contains(), add(), remove()
    }
    
    public void collectionExample() {
        // List: O(1) access for ArrayList, ordered
        List<String> list = new ArrayList<>(); // grows dynamically
        list.add("Alice"); 
        list.add("Bob");
        list.add(5, "Diana"); // add at position, others shift
        System.out.println(list.get(0)); // O(1) for ArrayList
        System.out.println(list.contains("Bob")); // O(n) search
        
        // Set: unique elements, variable access time
        Set<String> set = new HashSet<>(); // O(1) average access
        set.add("apple");
        set.add("apple"); // duplicate ignored
        
        // Map: key-value pairs, O(1) average access
        Map<String, Integer> map = new HashMap<>();
        map.put("Alice", 30); // O(1) average insertion
        System.out.println(map.get("Alice")); // O(1) average retrieval
    }
    
    public void performanceComparison() {
        // Arrays: faster, fixed memory
        long[] arrayData = new long[1_000_000];
        long start = System.nanoTime();
        for (int i = 0; i < arrayData.length; i++) {
            arrayData[i] = i * 2; // direct memory access
        }
        long arrayTime = System.nanoTime() - start;
        
        // ArrayList: slower, more overhead
        List<Long> listData = new ArrayList<>();
        start = System.nanoTime();
        for (int i = 0; i < 1_000_000; i++) {
            listData.add((long) i * 2); // boxing, potential resizing
        }
        long listTime = System.nanoTime() - start;
        
        System.out.println("Array time: " + arrayTime + " ns");
        System.out.println("ArrayList time: " + listTime + " ns");
    }
    
    public void threadSafetyExample() {
        // Not thread-safe
        String[] array = {"A", "B", "C"};
        List<String> unsafeList = new ArrayList<>();
        
        // Thread-safe alternatives
        Map<String, Integer> syncMap = new ConcurrentHashMap<>();
        List<String> syncList = Collections.synchronizedList(new ArrayList<>());
        
        for (int i = 0; i < 100; i++) {
            syncMap.put("key" + i, i);
            syncList.add("item" + i);
        }
    }
    
    public void recommendedUsage() {
        // Use Array: fixed size, maximum performance, primitives
        int[] primes = {2, 3, 5, 7, 11};
        
        // Use Collection: dynamic size, flexibility, type safety
        List<Integer> dynamicNumbers = new ArrayList<>();
        dynamicNumbers.add(2);
        dynamicNumbers.remove(0);
    }
}
```

### Keywords/Tags
- java-collections
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
