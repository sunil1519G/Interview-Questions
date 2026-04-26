# Java Interview Questions (Advanced)

Source PDF: `Java Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. How do `synchronized`, `Lock`, and concurrent collections help in thread-safe Java applications?](#q-1)
<a id="q-1"></a>
## 1. Question
How do `synchronized`, `Lock`, and concurrent collections help in thread-safe Java applications?

### Answer
`synchronized` provides implicit mutual exclusion via intrinsic locks (monitors) but can suffer from deadlocks and offers no fairness guarantees. `Lock` (via `ReentrantLock`) provides explicit control, timeout support, fairness options, and interruptibility. Concurrent collections (ConcurrentHashMap, CopyOnWriteArrayList) use fine-grained locking or lock-free algorithms to allow multiple threads to access different segments simultaneously, reducing contention. The JMM (Java Memory Model) defines happens-before relationships: volatile writes establish memory barriers ensuring visibility across threads; synchronized actions on the same lock establish mutual exclusion. Choose based on contention: high contention → concurrent collections; complex logic → Lock; simple access → synchronized.

### Code Snippet
```java
import java.util.concurrent.*;
import java.util.concurrent.locks.*;
import java.util.*;

// 1. Synchronized: intrinsic locks (implicit)
public class SynchronizedCounter {
    private int count = 0;
    
    public synchronized void increment() {
        count++; // entire method is protected by intrinsic lock on 'this'
    }
    
    public synchronized int getCount() {
        return count;
    }
    
    // Block-level synchronization: finer granularity
    public void incrementIfNeed() {
        synchronized (this) {
            count++; // only this block is locked, reduces hold time
        }
    }
}

// 2. Lock: explicit control, more powerful
public class LockBasedCounter {
    private int count = 0;
    private final Lock lock = new ReentrantLock(); // explicit lock
    
    public void increment() {
        lock.lock(); // acquire lock (may wait indefinitely)
        try {
            count++; // critical section
        } finally {
            lock.unlock(); // ALWAYS unlock in finally
        }
    }
    
    public int getCountWithTimeout() throws InterruptedException {
        // tryLock with timeout: avoid indefinite waiting
        if (lock.tryLock(100, TimeUnit.MILLISECONDS)) {
            try {
                return count;
            } finally {
                lock.unlock();
            }
        }
        return -1; // timeout
    }
    
    // Condition: wait-notify equivalent with more control
    private Condition notFull = lock.newCondition();
    public void waitUntilCondition() throws InterruptedException {
        lock.lock();
        try {
            while (count >= 100) {
                notFull.await(); // thread waits on condition
            }
            count++;
            notFull.signalAll(); // notify waiting threads
        } finally {
            lock.unlock();
        }
    }
}

// 3. Concurrent Collections: lock-free/segmented access
public class ConcurrentCollectionsExample {
    
    public void demonstrateConcurrentHashMap() {
        // ConcurrentHashMap: segment-based locking, multiple threads can access different buckets
        ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
        
        // Thread A accesses segment 0
        new Thread(() -> {
            for (int i = 0; i < 1000; i++) {
                map.put("key" + i, i);
            }
        }).start();
        
        // Thread B accesses different segment without blocking Thread A
        new Thread(() -> {
            for (int i = 1000; i < 2000; i++) {
                map.get("key" + (i - 500)); // concurrent reads, no contention
            }
        }).start();
        
        // Single lock on full table would serialize all accesses (bad)
        // ConcurrentHashMap divides into segments for parallel access
    }
    
    public void demonstrateCopyOnWriteArrayList() {
        // CopyOnWriteArrayList: optimal for read-heavy workloads
        CopyOnWriteArrayList<String> list = new CopyOnWriteArrayList<>();
        
        // Reads don't require synchronization
        new Thread(() -> {
            for (String item : list) {
                System.out.println(item); // no lock, fast
            }
        }).start();
        
        // Writes copy entire array (expensive but rare)
        new Thread(() -> {
            list.add("new item"); // creates copy under the hood
        }).start();
        
        // Use case: observers list, event listeners (many readers, few writers)
    }
}

// 4. Memory Model: visibility guarantees
public class MemoryVisibilityExample {
    
    // WITHOUT synchronization: no guarantee reader sees writer's change
    public static class UnsafeVisibility {
        private int flag = 0;
        private String message = "";
        
        public void writer() {
            message = "Hello"; // might not be visible to reader
            flag = 1;
        }
        
        public void reader() {
            if (flag == 1) {
                System.out.println(message); // might print ""; or stale value
            }
        }
    }
    
    // WITH volatile: guarantees visibility
    public static class SafeVisibility {
        private volatile int flag = 0; // volatile creates memory barrier
        private String message = ""; // safely published via volatile flag
        
        public void writer() {
            message = "Hello";
            flag = 1; // volatile write: flushes all prior writes to main memory
        }
        
        public void reader() {
            if (flag == 1) { // volatile read: invalidates cache, reads from main memory
                System.out.println(message); // GUARANTEED to see "Hello"
            }
        }
    }
    
    // WITH synchronized: mutual exclusion + visibility
    public static class SynchronizedVisibility {
        private int flag = 0;
        private String message = "";
        
        public synchronized void writer() {
            message = "Hello";
            flag = 1;
            // synchronized exit: memory barrier, writes flushed
        }
        
        public synchronized void reader() {
            if (flag == 1) {
                System.out.println(message); // synchronized entry: cache invalidated
            }
        }
    }
}

// 5. Performance comparison
public class ConcurrencyPerformanceComparison {
    static final int ITERATIONS = 10_000_000;
    
    public static void main(String[] args) {
        // Synchronized: high contention on single lock
        long syncTime = measureSynchronized();
        
        // Lock: similar to synchronized, but with more options
        long lockTime = measureLock();
        
        // Concurrent: minimal contention
        long concurrentTime = measureConcurrent();
        
        System.out.println("Synchronized: " + syncTime + "ms");
        System.out.println("Lock: " + lockTime + "ms");
        System.out.println("Concurrent: " + concurrentTime + "ms");
        // Concurrent collections should be significantly faster under contention
    }
    
    static long measureSynchronized() {
        SynchronizedCounter counter = new SynchronizedCounter();
        long start = System.currentTimeMillis();
        
        Thread[] threads = new Thread[4];
        for (int i = 0; i < 4; i++) {
            threads[i] = new Thread(() -> {
                for (int j = 0; j < ITERATIONS; j++) {
                    counter.increment();
                }
            });
            threads[i].start();
        }
        
        for (Thread t : threads) {
            try {
                t.join();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        
        return System.currentTimeMillis() - start;
    }
    
    static long measureLock() {
        LockBasedCounter counter = new LockBasedCounter();
        long start = System.currentTimeMillis();
        
        // similar threading code
        return System.currentTimeMillis() - start;
    }
    
    static long measureConcurrent() {
        ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
        long start = System.currentTimeMillis();
        
        Thread[] threads = new Thread[4];
        for (int i = 0; i < 4; i++) {
            final int threadNum = i;
            threads[i] = new Thread(() -> {
                for (int j = 0; j < ITERATIONS; j++) {
                    map.put("key" + threadNum + "_" + j, j);
                }
            });
            threads[i].start();
        }
        
        for (Thread t : threads) {
            try {
                t.join();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
        
        return System.currentTimeMillis() - start;
    }
}
```

### Keywords/Tags
- java
- advanced
- concurrency
- thread-safety

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
