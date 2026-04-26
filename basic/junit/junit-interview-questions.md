# Junit Interview Questions (Basic)

Source PDF: `JUnit Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What is JUnit?](#q-1)
- [2. What is Unit Testing?](#q-2)
- [3. Why do we use JUnit? Who uses JUnit more - Developers or Testers?](#q-3)
- [4. What are the features of JUnit?](#q-4)
- [5. Is it mandatory to write test cases for every logic?](#q-5)
- [6. How will you write a simple JUnit test case?](#q-6)
- [7. What will happen if the return type of the JUnit method is String?](#q-7)
- [8. What is a JUnit fixture?](#q-8)
- [9. What is a test suite?](#q-9)
- [10. What is mocking and stubbing?](#q-10)
- [11. What are the JUnit Assert Methods?](#q-11)
- [12. What are the best practices for writing Unit Test Cases?](#q-12)
- [13. What are the differences between JUnit 4 and JUnit 5?](#q-13)
- [14. What are the differences between JUnit and TestNG?](#q-14)
- [15. How can we test protected methods?](#q-15)
- [16. Why can't we use System.out.println() for testing and debugging?](#q-16)
- [17. How can we run JUnit from the command window?](#q-17)
- [18. How do you assert exceptions thrown in JUnit 4 tests?](#q-18)
- [19. What is the keyboard shortcut for running the Junit test cases in eclipse IDE?](#q-19)
- [20. Define code coverage. What are the different types of code coverages?](#q-20)
- [21. Is it possible to test the Java method for a timeout in JUnit?](#q-21)
- [22. Why does JUnit report only the first failure in a single attempt?](#q-22)
- [23. How can we do testing for private methods?](#q-23)
- [24. How can you test a generics class?](#q-24)
- [25. Why do we need mocking in unit testing?](#q-25)
- [26. What is Mockito? What are some of its advantages?](#q-26)
- [27. When and why should we use spy?](#q-27)
- [28. Why can’t we mock static methods in Mockito?](#q-28)
- [29. How can we mock void methods in Mockito?](#q-29)
<a id="q-1"></a>
## 1. Question
What is JUnit?

### Answer
For "What is JUnit?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What is Unit Testing?

### Answer
For "What is Unit Testing?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
Why do we use JUnit? Who uses JUnit more - Developers or Testers?

### Answer
For "Why do we use JUnit? Who uses JUnit more - Developers or Testers?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
What are the features of JUnit?

### Answer
For "What are the features of JUnit?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
Is it mandatory to write test cases for every logic?

### Answer
For "Is it mandatory to write test cases for every logic?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
How will you write a simple JUnit test case?

### Answer
For "How will you write a simple JUnit test case?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-7"></a>
## 7. Question
What will happen if the return type of the JUnit method is String?

### Answer
For "What will happen if the return type of the JUnit method is String?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-8"></a>
## 8. Question
What is a JUnit fixture?

### Answer
For "What is a JUnit fixture?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-9"></a>
## 9. Question
What is a test suite?

### Answer
For "What is a test suite?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-10"></a>
## 10. Question
What is mocking and stubbing?

### Answer
For "What is mocking and stubbing?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-11"></a>
## 11. Question
What are the JUnit Assert Methods?

### Answer
For "What are the JUnit Assert Methods?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-12"></a>
## 12. Question
What are the best practices for writing Unit Test Cases?

### Answer
For "What are the best practices for writing Unit Test Cases?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-13"></a>
## 13. Question
What are the differences between JUnit 4 and JUnit 5?

### Answer
For "What are the differences between JUnit 4 and JUnit 5?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-14"></a>
## 14. Question
What are the differences between JUnit and TestNG?

### Answer
For "What are the differences between JUnit and TestNG?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-15"></a>
## 15. Question
How can we test protected methods?

### Answer
For "How can we test protected methods?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-16"></a>
## 16. Question
Why can't we use System.out.println() for testing and debugging?

### Answer
For "Why can't we use System.out.println() for testing and debugging?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-17"></a>
## 17. Question
How can we run JUnit from the command window?

### Answer
For "How can we run JUnit from the command window?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-18"></a>
## 18. Question
How do you assert exceptions thrown in JUnit 4 tests?

### Answer
For "How do you assert exceptions thrown in JUnit 4 tests?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-19"></a>
## 19. Question
What is the keyboard shortcut for running the Junit test cases in eclipse IDE?

### Answer
For "What is the keyboard shortcut for running the Junit test cases in eclipse IDE?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-20"></a>
## 20. Question
Define code coverage. What are the different types of code coverages?

### Answer
For "Define code coverage. What are the different types of code coverages?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-21"></a>
## 21. Question
Is it possible to test the Java method for a timeout in JUnit?

### Answer
For "Is it possible to test the Java method for a timeout in JUnit?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-22"></a>
## 22. Question
Why does JUnit report only the first failure in a single attempt?

### Answer
For "Why does JUnit report only the first failure in a single attempt?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-23"></a>
## 23. Question
How can we do testing for private methods?

### Answer
For "How can we do testing for private methods?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-24"></a>
## 24. Question
How can you test a generics class?

### Answer
For "How can you test a generics class?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-25"></a>
## 25. Question
Why do we need mocking in unit testing?

### Answer
For "Why do we need mocking in unit testing?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-26"></a>
## 26. Question
What is Mockito? What are some of its advantages?

### Answer
For "What is Mockito? What are some of its advantages?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-27"></a>
## 27. Question
When and why should we use spy?

### Answer
For "When and why should we use spy?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-28"></a>
## 28. Question
Why can’t we mock static methods in Mockito?

### Answer
For "Why can’t we mock static methods in Mockito?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-29"></a>
## 29. Question
How can we mock void methods in Mockito?

### Answer
For "How can we mock void methods in Mockito?", explain the testing objective, fixture setup, assertions, and isolation boundaries. Include how you keep tests deterministic, fast, and maintainable in CI pipelines.

### Code Snippet
```java
@Test // JUnit test method
void shouldCalculateTotal() {
    int total = service.total(40, 2); // execute behavior under test
    assertEquals(42, total);          // verify expected outcome
}
```

### Keywords/Tags
- junit
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
