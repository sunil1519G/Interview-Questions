# Java Interview Questions (Basic)

Source PDF: `Java Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. Why is Java a platform independent language?](#q-1)
- [2. Why is Java not a pure object oriented language?](#q-2)
- [3. Can java be said to be the complete object-oriented programming language?](#q-3)
- [4. How is Java different from C++?](#q-4)
- [5. Pointers are used in C/ C++. Why does Java not make use of pointers?](#q-5)
- [6. What do you understand by an instance variable and a local variable?](#q-6)
- [7. What are the default values assigned to variables and instances in java?](#q-7)
- [8. What do you mean by data encapsulation?](#q-8)
- [9. How is an infinite loop declared in Java?](#q-9)
- [10. Can the main method be Overloaded?](#q-10)
- [11. Do final, finally and finalize keywords have the same function?](#q-11)
- [12. When can you use super keyword?](#q-12)
- [13. Can the static methods be overloaded?](#q-13)
- [14. Why is the main method static in Java?](#q-14)
- [15. Can the static methods be overridden?](#q-15)
- [16. What is the main objective of garbage collection?](#q-16)
- [17. What is a ClassLoader?](#q-17)
- [18. What part of memory - Stack or Heap - is cleaned in garbage collection process?](#q-18)
- [19. What are shallow copy and deep copy in java?](#q-19)
- [20. What is a Comparator in java?](#q-20)
- [21. What makes a HashSet different from a TreeSet?](#q-21)
- [22. What do we get in the JDK file?](#q-22)
- [23. What are the differences between JVM, JRE and JDK in Java?](#q-23)
- [24. What are the differences between HashMap and HashTable in Java?](#q-24)
- [25. What is the importance of reflection in Java?](#q-25)
- [26. What are the different ways of threads usage?](#q-26)
- [27. What are the differences between constructor and method of a class in Java?](#q-27)
- [28. Java works as “pass by value” or “pass by reference” phenomenon?](#q-28)
- [29. What is the ‘IS-A ‘ relationship in OOPs java?](#q-29)
- [30. Can we make the main() thread a daemon thread?](#q-30)
- [31. What happens if there are multiple main methods inside one class in Java?](#q-31)
- [32. What do you understand by Object Cloning and how do you achieve it in Java?](#q-32)
- [33. How do exceptions affect the program if it doesn't handle them?](#q-33)
- [34. Is it mandatory for a catch block to be followed aer a try block?](#q-34)
- [35. Can you call a constructor of a class inside the another constructor?](#q-35)
- [36. Why does the java array index start with 0?](#q-36)
- [37. Why is the remove method faster in the linked list than in an array?](#q-37)
- [38. How is the creation of a String using new() different from that of a literal?](#q-38)
- [39. How is the ‘new’ operator different from the ‘newInstance()’ operator in java?](#q-39)
- [40. In the given code below, what is the significance of ... ?](#q-40)
- [41. Can you explain the Java thread lifecycle?](#q-41)
- [42. What do you understand by marker interfaces in Java?](#q-42)
- [43. Explain the term “Double Brace Initialisation” in Java?](#q-43)
- [44. What is the output of the below code and why?](#q-44)
- [45. How we can set the spring bean scope. And what supported scopes does it have?](#q-45)
- [46. What are the different types of Thread Priorities in Java?](#q-46)
- [47. What are variables in Java, and what are the differences between primitive and reference variables?](#q-47)
- [48. What are control flow statements in Java, and when should you use `if`, `switch`, and loops?](#q-48)
<a id="q-1"></a>
## 1. Question
Why is Java a platform independent language?

### Answer
Java compiles source code into bytecode (`.class`) that runs on any OS with a compatible JVM. The JVM abstracts OS/hardware differences, so the same binary can run across platforms.

### Code Snippet
```java
System.out.println(System.getProperty("java.version")); // JVM version
System.out.println(System.getProperty("os.name"));      // OS name
// Same bytecode can run on any OS with a compatible JVM
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
Why is Java not a pure object oriented language?

### Answer
Java is not considered purely object-oriented because it has primitive types (`int`, `boolean`, etc.) that are not objects. It is strongly object-oriented in design, but primitives exist for performance and simplicity.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
Can java be said to be the complete object-oriented programming language?

### Answer
Java is not considered purely object-oriented because it has primitive types (`int`, `boolean`, etc.) that are not objects. It is strongly object-oriented in design, but primitives exist for performance and simplicity.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
How is Java different from C++?

### Answer
Java removes several C++ features (pointer arithmetic, multiple inheritance of classes, manual memory management) and adds JVM-based portability with automatic garbage collection. C++ offers lower-level control; Java prioritizes safety and portability.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
Pointers are used in C/ C++. Why does Java not make use of pointers?

### Answer
Java hides pointers to improve memory safety and prevent arbitrary memory access. References are still used, but pointer arithmetic is not exposed to developers.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
What do you understand by an instance variable and a local variable?

### Answer
Instance variables belong to an object and live as long as the object exists. Local variables are method-scoped, live only during method execution, and must be initialized before use.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-7"></a>
## 7. Question
What are the default values assigned to variables and instances in java?

### Answer
Instance and static fields get default values (`0`, `false`, `null`). Local variables do not get defaults and must be explicitly initialized before access.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-8"></a>
## 8. Question
What do you mean by data encapsulation?

### Answer
Encapsulation means bundling data with behavior and restricting direct access using access modifiers. It protects invariants and exposes controlled APIs via getters/setters or domain methods.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-9"></a>
## 9. Question
How is an infinite loop declared in Java?

### Answer
An infinite loop is commonly written as `while (true)` or `for(;;)`. It should be used only when loop exit is controlled internally (for example, event loops or polling with break conditions).

### Code Snippet
```java
while (true) {
    // poll queue/events continuously
    if (Thread.currentThread().isInterrupted()) break; // safe exit condition
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-10"></a>
## 10. Question
Can the main method be Overloaded?

### Answer
Yes, `main` can be overloaded, but JVM entry point is only `public static void main(String[] args)`. Other overloads are normal methods and are not called automatically at startup.

### Code Snippet
```java
public class App {
    public static void main(String[] args) { // JVM entry point
        main(1); // overloaded main can be called manually
    }
    static void main(int version) { System.out.println(version); }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-11"></a>
## 11. Question
Do final, finally and finalize keywords have the same function?

### Answer
`final` is a keyword for constants/inheritance control, `finally` is an exception-handling block, and `finalize()` was an old GC hook now deprecated for removal. They are unrelated in purpose.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-12"></a>
## 12. Question
When can you use super keyword?

### Answer
`super` refers to parent class members. It is used to call superclass constructors (`super(...)`), access overridden fields/methods, and disambiguate inherited behavior.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-13"></a>
## 13. Question
Can the static methods be overloaded?

### Answer
Yes. Static methods can be overloaded by changing parameter lists. Overloading is compile-time method resolution and works for both static and instance methods.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-14"></a>
## 14. Question
Why is the main method static in Java?

### Answer
JVM calls `main` before creating any object. Making it `static` allows invocation without an instance of the class.

### Code Snippet
```java
public class App {
    public static void main(String[] args) { // JVM entry point
        main(1); // overloaded main can be called manually
    }
    static void main(int version) { System.out.println(version); }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-15"></a>
## 15. Question
Can the static methods be overridden?

### Answer
Static methods are not overridden; they are hidden. Method call selection depends on reference type, not runtime object type.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-16"></a>
## 16. Question
What is the main objective of garbage collection?

### Answer
Garbage collection reclaims heap memory from unreachable objects, reducing manual memory management bugs. It improves safety but does not prevent logical memory leaks caused by retained references.

### Code Snippet
```java
Object ref = new Object();
ref = null; // object becomes eligible for GC (not immediate collection)
System.gc(); // only a request to JVM, not guaranteed
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-17"></a>
## 17. Question
What is a ClassLoader?

### Answer
ClassLoader loads class bytecode into the JVM at runtime. It follows delegation (Bootstrap -> Platform -> Application) and enables modular loading and isolation.

### Code Snippet
```java
ClassLoader loader = String.class.getClassLoader();
System.out.println(loader); // null for bootstrap-loaded classes
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-18"></a>
## 18. Question
What part of memory - Stack or Heap - is cleaned in garbage collection process?

### Answer
Garbage collection reclaims heap memory from unreachable objects, reducing manual memory management bugs. It improves safety but does not prevent logical memory leaks caused by retained references.

### Code Snippet
```java
Object ref = new Object();
ref = null; // object becomes eligible for GC (not immediate collection)
System.gc(); // only a request to JVM, not guaranteed
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-19"></a>
## 19. Question
What are shallow copy and deep copy in java?

### Answer
Shallow copy duplicates object references; nested mutable objects are shared. Deep copy recursively duplicates nested objects so original and copy are fully independent.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-20"></a>
## 20. Question
What is a Comparator in java?

### Answer
`Comparator<T>` defines external/custom ordering logic, often used for sorting (`Collections.sort`, streams). It avoids modifying the class itself (unlike `Comparable`).

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-21"></a>
## 21. Question
What makes a HashSet different from a TreeSet?

### Answer
`HashSet` is hash-based with average O(1) operations and no ordering guarantees. `TreeSet` is tree-based (sorted order) with O(log n) operations.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-22"></a>
## 22. Question
What do we get in the JDK file?

### Answer
JDK includes JRE + development tools such as `javac`, `jar`, `javadoc`, `jdb`, and monitoring tools. It is used to build, run, and debug Java applications.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-23"></a>
## 23. Question
What are the differences between JVM, JRE and JDK in Java?

### Answer
JVM executes bytecode. JRE provides JVM + runtime libraries. JDK provides JRE + compiler and developer tooling.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-24"></a>
## 24. Question
What are the differences between HashMap and HashTable in Java?

### Answer
`HashMap` is non-synchronized and allows null key/value(s). `Hashtable` is synchronized, legacy, and disallows null keys/values. Prefer `ConcurrentHashMap` for modern concurrent use.

### Code Snippet
```java
Map<String, Integer> map = new HashMap<>(); // non-synchronized
map.put(null, 1); // HashMap allows one null key

Map<String, Integer> table = new Hashtable<>();
// table.put(null, 1); // would throw NullPointerException
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-25"></a>
## 25. Question
What is the importance of reflection in Java?

### Answer
Reflection lets code inspect and invoke classes/methods/fields at runtime. It is useful in frameworks, DI, and serialization, but has performance and maintainability costs.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-26"></a>
## 26. Question
What are the different ways of threads usage?

### Answer
Threads can be created by extending `Thread`, implementing `Runnable`, or preferably using executors (`ExecutorService`) for pooling and lifecycle management.

### Code Snippet
```java
ExecutorService pool = Executors.newFixedThreadPool(2); // thread pool
pool.submit(() -> System.out.println("Task running")); // async task
pool.shutdown(); // graceful termination
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-27"></a>
## 27. Question
What are the differences between constructor and method of a class in Java?

### Answer
Constructors initialize new objects and have no return type; methods define behavior and can be called repeatedly on existing objects.

### Code Snippet
```java
class Person {
    Person() { this("Unknown"); } // constructor chaining using this(...)
    Person(String name) { /* initialize fields */ }
    void greet() { System.out.println("Hello"); } // regular method
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-28"></a>
## 28. Question
Java works as “pass by value” or “pass by reference” phenomenon?

### Answer
Java is strictly pass-by-value. For objects, the value passed is the reference copy, so methods can mutate object state but cannot rebind caller references.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-29"></a>
## 29. Question
What is the ‘IS-A ‘ relationship in OOPs java?

### Answer
`IS-A` represents inheritance/polymorphism (e.g., `Dog IS-A Animal`). It models specialization and allows substitutability where parent type is expected.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-30"></a>
## 30. Question
Can we make the main() thread a daemon thread?

### Answer
You can mark a thread as daemon using `setDaemon(true)` before starting it. JVM exits when only daemon threads remain.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-31"></a>
## 31. Question
What happens if there are multiple main methods inside one class in Java?

### Answer
A class can contain overloaded `main` methods, but JVM calls only the exact signature `public static void main(String[] args)` as entry point.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-32"></a>
## 32. Question
What do you understand by Object Cloning and how do you achieve it in Java?

### Answer
Object cloning creates a copy of an object, usually via `clone()` and `Cloneable`, but many teams prefer copy constructors or builders for clarity and safety.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-33"></a>
## 33. Question
How do exceptions affect the program if it doesn't handle them?

### Answer
Unchecked exceptions propagate up the call stack and can terminate the thread if unhandled. Proper handling/logging prevents abrupt failures and improves reliability.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-34"></a>
## 34. Question
Is it mandatory for a catch block to be followed aer a try block?

### Answer
No. A `try` block must be followed by at least one `catch` or a `finally` block (or both). `try` alone is invalid.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-35"></a>
## 35. Question
Can you call a constructor of a class inside the another constructor?

### Answer
Yes, constructor chaining is supported using `this(...)` (same class) or `super(...)` (parent class), and it must be the first statement in the constructor.

### Code Snippet
```java
class Person {
    Person() { this("Unknown"); } // constructor chaining using this(...)
    Person(String name) { /* initialize fields */ }
    void greet() { System.out.println("Hello"); } // regular method
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-36"></a>
## 36. Question
Why does the java array index start with 0?

### Answer
Zero-based indexing maps directly to memory offset calculation (`base + index * size`), simplifying implementation and improving performance consistency.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-37"></a>
## 37. Question
Why is the remove method faster in the linked list than in an array?

### Answer
Removal in linked lists can be O(1) once node reference is known; arrays require element shifting O(n). But linked-list search is O(n), so real performance depends on access pattern.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-38"></a>
## 38. Question
How is the creation of a String using new() different from that of a literal?

### Answer
String literals are interned in the string pool and may share instances. `new String(...)` always creates a new object on heap, even if equivalent literal exists.

### Code Snippet
```java
String s1 = "java";              // interned literal in string pool
String s2 = new String("java");  // new heap object
System.out.println(s1 == s2);     // false (different references)
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-39"></a>
## 39. Question
How is the ‘new’ operator different from the ‘newInstance()’ operator in java?

### Answer
Explain the concept with definition, JVM/runtime behavior, and one practical example including a typical interview pitfall.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-40"></a>
## 40. Question
In the given code below, what is the significance of ... ?

### Answer
Explain the concept with definition, JVM/runtime behavior, and one practical example including a typical interview pitfall.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-41"></a>
## 41. Question
Can you explain the Java thread lifecycle?

### Answer
Thread lifecycle states include NEW, RUNNABLE, BLOCKED/WAITING/TIMED_WAITING, and TERMINATED. State transitions depend on scheduler, locks, sleeps, and completion.

### Code Snippet
```java
ExecutorService pool = Executors.newFixedThreadPool(2); // thread pool
pool.submit(() -> System.out.println("Task running")); // async task
pool.shutdown(); // graceful termination
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-42"></a>
## 42. Question
What do you understand by marker interfaces in Java?

### Answer
Marker interfaces have no methods and convey metadata to JVM/frameworks (e.g., `Serializable`, `Cloneable`). They signal capabilities or special handling.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-43"></a>
## 43. Question
Explain the term “Double Brace Initialisation” in Java?

### Answer
Double-brace initialization creates an anonymous class with an instance initializer. It is concise but discouraged due to extra class creation, hidden references, and memory overhead.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-44"></a>
## 44. Question
What is the output of the below code and why?

### Answer
Explain the concept with definition, JVM/runtime behavior, and one practical example including a typical interview pitfall.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-45"></a>
## 45. Question
How we can set the spring bean scope. And what supported scopes does it have?

### Answer
Common Spring bean scopes are `singleton` (default), `prototype`, `request`, `session`, and `application` (web contexts). Scope controls object lifecycle and sharing behavior.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-46"></a>
## 46. Question
What are the different types of Thread Priorities in Java?

### Answer
Java thread priorities range from 1 (MIN_PRIORITY) to 10 (MAX_PRIORITY), default 5. Priorities are scheduler hints, not strict execution guarantees.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-47"></a>
## 47. Question
What are variables in Java, and what are the differences between primitive and reference variables?

### Answer
Primitive variables store actual values (e.g., `int`, `boolean`), while reference variables store object references. References point to heap objects; primitives are value types.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-48"></a>
## 48. Question
What are control flow statements in Java, and when should you use `if`, `switch`, and loops?

### Answer
Control flow statements (`if`, `switch`, loops) define execution paths. Use `if/switch` for branching and loops (`for`, `while`) for repetition based on conditions.

### Code Snippet
```java
// Minimal runnable Java snippet with clear behavior
public class Example {
    public static void main(String[] args) {
        int version = 21; // sample primitive value
        String runtime = "JVM"; // sample reference value
        System.out.println(runtime + " version " + version); // demonstration output
    }
}
```

### Keywords/Tags
- java
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
