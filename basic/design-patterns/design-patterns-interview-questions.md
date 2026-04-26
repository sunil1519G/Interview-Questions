# Design Patterns Interview Questions (Basic)

Source PDF: `Design Patterns Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What is Inversion of Control?](#q-1)
- [2. What are the SOLID Principles?](#q-2)
- [3. What do you understand by the Open-Closed Principle (OCP)?](#q-3)
- [4. What is a Command pattern?](#q-4)
- [5. What problem does Builder Pattern try to solve?](#q-5)
- [6. What do you understand by the Null Object pattern?](#q-6)
- [7. What are the components of the Composite Entity pattern?](#q-7)
- [8. What is the Singleton pattern, and when is it useful?](#q-8)
- [9. How does the Factory pattern simplify object creation?](#q-9)
<a id="q-1"></a>
## 1. Question
What is Inversion of Control?

### Answer
Inversion of Control (IoC) means object creation and dependency wiring are delegated to a container/framework instead of being hardcoded in business classes. This lowers coupling and improves testability because implementations can be swapped via configuration or DI.

### Code Snippet
```java
interface PaymentService { void pay(); } // dependency contract

class CardPaymentService implements PaymentService {
    public void pay() { System.out.println("Paid by card"); }
}

class CheckoutController {
    private final PaymentService paymentService; // injected dependency
    CheckoutController(PaymentService paymentService) { this.paymentService = paymentService; }
}
```

### Keywords/Tags
- design-patterns
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What are the SOLID Principles?

### Answer
SOLID includes Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, and Dependency Inversion. These principles help teams design extensible and maintainable code by reducing rigid dependencies and improving substitution and modularity.

### Code Snippet
```java
interface DiscountStrategy { double apply(double amount); } // extension point

class FestiveDiscount implements DiscountStrategy {
    public double apply(double amount) { return amount * 0.9; } // new behavior without changing caller
}
```

### Keywords/Tags
- design-patterns
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
What do you understand by the Open-Closed Principle (OCP)?

### Answer
Open-Closed Principle states modules should be open for extension but closed for modification. Practically, you add new behavior with interfaces/strategies or composition, rather than repeatedly editing stable existing classes.

### Code Snippet
```java
interface DiscountStrategy { double apply(double amount); } // extension point

class FestiveDiscount implements DiscountStrategy {
    public double apply(double amount) { return amount * 0.9; } // new behavior without changing caller
}
```

### Keywords/Tags
- design-patterns
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
What is a Command pattern?

### Answer
Command pattern wraps a request as an object with an `execute()` operation. It decouples the invoker from concrete receivers and supports features like undo/redo, queued execution, retries, and audit logging.

### Code Snippet
```java
interface Command { void execute(); } // common command contract

class LightOnCommand implements Command {
    public void execute() { System.out.println("Light ON"); } // receiver action
}
```

### Keywords/Tags
- design-patterns
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
What problem does Builder Pattern try to solve?

### Answer
Builder solves the telescoping-constructor problem when objects have many optional fields. It enables readable step-by-step construction and can enforce object validity before `build()` returns the final immutable instance.

### Code Snippet
```java
User user = User.builder() // start fluent construction
    .name("Sunil")         // required/optional field
    .email("sunil@demo.com")
    .build();               // validate and create immutable object
```

### Keywords/Tags
- design-patterns
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
What do you understand by the Null Object pattern?

### Answer
Null Object pattern replaces `null` with a no-op implementation of the same interface. This removes repeated null checks, simplifies client logic, and reduces `NullPointerException` risks.

### Code Snippet
```java
interface Logger { void info(String msg); }
class NoOpLogger implements Logger {
    public void info(String msg) { /* intentionally do nothing */ }
}
```

### Keywords/Tags
- design-patterns
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-7"></a>
## 7. Question
What are the components of the Composite Entity pattern?

### Answer
Composite Entity pattern is used to model a coarse-grained object composed of dependent objects. Typical participants are Composite Entity, Coarse-Grained Object, Dependent Object(s), and strategy/access components that update dependents consistently.

### Code Snippet
```java
class DependentObjectA { String data; }
class DependentObjectB { String data; }

class CoarseGrainedObject {
    DependentObjectA a = new DependentObjectA();
    DependentObjectB b = new DependentObjectB();
    void setData(String x, String y) { a.data = x; b.data = y; } // update dependents together
}
```

### Keywords/Tags
- design-patterns
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-8"></a>
## 8. Question
What is the Singleton pattern, and when is it useful?

### Answer
Singleton ensures only one instance of a class exists and provides global access to it. It is useful for shared stateless resources (configuration, registry, logger) but should be used carefully because global state can hurt testability.

### Code Snippet
```java
public enum AppConfig {
    INSTANCE; // enum singleton is thread-safe by JVM design

    public String get(String key) { return "value"; }
}
```

### Keywords/Tags
- design-patterns
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-9"></a>
## 9. Question
How does the Factory pattern simplify object creation?

### Answer
Factory centralizes object creation behind an abstraction, so callers depend on interfaces instead of concrete classes. This improves extensibility, because adding a new implementation usually changes factory logic only, not client code.

### Code Snippet
```java
interface Notification { void send(); } // common product interface
class EmailNotification implements Notification {
    public void send() { System.out.println("Email sent"); }
}
class NotificationFactory {
    static Notification create(String type) { return new EmailNotification(); } // centralized creation
}
```

### Keywords/Tags
- design-patterns
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
