# Java Interview Questions (Intermediate)

Source PDF: `Java Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What is a singleton class in Java? And How to implement a singleton class?](#q-1)
- [2. What is the difference between the program and the process?](#q-2)
- [3. What is the difference between the ‘throw’ and ‘throws’ keyword in java?](#q-3)
- [4. How to not allow serialization of attributes of a class in Java?](#q-4)
- [5. How does an exception propagate in the code?](#q-5)
- [6. What is the difference between ‘>>’ and ‘>>>’ operators in java?](#q-6)
- [7. What are the different categories of Java Design patterns?](#q-7)
<a id="q-1"></a>
## 1. Question
What is a singleton class in Java? And How to implement a singleton class?

### Answer
A singleton class ensures exactly one instance in the JVM and provides a global access point. In Java, enum-based singleton is the safest approach because it is thread-safe and resistant to reflection/serialization issues.

### Code Snippet
```java
public enum ConfigManager {
    INSTANCE; // JVM guarantees a single instance

    public String get(String key) { return "demo"; }
}
```

### Keywords/Tags
- java
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What is the difference between the program and the process?

### Answer
A program is a passive executable definition on disk; a process is an active running instance of a program with its own memory space and runtime state. Multiple processes can run from the same program.

### Code Snippet
```java
System.out.println("Program started"); // compiled program instructions
long pid = ProcessHandle.current().pid();
System.out.println("Running as process: " + pid); // active OS process id
```

### Keywords/Tags
- java
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
What is the difference between the ‘throw’ and ‘throws’ keyword in java?

### Answer
`throw` is used inside a method/body to explicitly raise an exception object. `throws` is used in a method signature to declare that the method may propagate specific checked exceptions to the caller.

### Code Snippet
```java
void readFile(String path) throws IOException { // declaration to caller
    if (path == null) {
        throw new IllegalArgumentException("path cannot be null"); // explicit throw
    }
}
```

### Keywords/Tags
- java
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
How to not allow serialization of attributes of a class in Java?

### Answer
Mark fields `transient` to exclude them from default Java serialization. For stricter control, implement custom `writeObject/readObject` methods or avoid Java native serialization in favor of explicit DTO mapping.

### Code Snippet
```java
class UserSession implements Serializable {
    private String userId;
    private transient String authToken; // excluded from serialization for security
}
```

### Keywords/Tags
- java
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
How does an exception propagate in the code?

### Answer
When an exception is thrown, JVM searches for a matching `catch` in the current call frame. If none is found, stack unwinding continues up the call stack until handled; otherwise the thread terminates with stack trace.

### Code Snippet
```java
void level1() { level2(); }
void level2() { throw new RuntimeException("boom"); } // propagates upward if uncaught

try { level1(); } catch (RuntimeException ex) { System.out.println(ex.getMessage()); }
```

### Keywords/Tags
- java
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
What is the difference between ‘>>’ and ‘>>>’ operators in java?

### Answer
`>>` is signed right shift and preserves the sign bit (arithmetic shift). `>>>` is unsigned right shift and fills left bits with zero (logical shift), which changes behavior for negative numbers.

### Code Snippet
```java
int n = -8;
System.out.println(n >> 1);  // signed shift: keeps sign bit
System.out.println(n >>> 1); // unsigned shift: fills with zeros
```

### Keywords/Tags
- java
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-7"></a>
## 7. Question
What are the different categories of Java Design patterns?

### Answer
Java design patterns are broadly categorized as Creational (object creation), Structural (composition/relationships), and Behavioral (interaction/responsibility flow). Choosing the right category depends on whether your problem is creation, structure, or behavior.

### Code Snippet
```java
// Creational: Builder/Factory
// Structural: Adapter/Decorator
// Behavioral: Strategy/Observer
System.out.println("Patterns grouped by creation, structure, and behavior");
```

### Keywords/Tags
- java
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
