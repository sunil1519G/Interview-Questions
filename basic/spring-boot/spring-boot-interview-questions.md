# Spring Boot Interview Questions (Basic)

Source PDF: `Springboot Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What are the advantages of using Spring Boot?](#q-1)
- [2. What are the Spring Boot key components?](#q-2)
- [3. Why Spring Boot over Spring?](#q-3)
- [4. What is the purpose of using @ComponentScan in the class files?](#q-4)
- [5. What are starter dependencies?](#q-5)
- [6. What is Spring Initializer?](#q-6)
- [7. What is Spring Boot CLI and what are its benefits?](#q-7)
- [8. What are the most common Spring Boot CLI commands?](#q-8)
- [9. Can we create a non-web application in Spring Boot?](#q-9)
- [10. Is it possible to change the port of the embedded Tomcat server in Spring Boot?](#q-10)
- [11. What is the default port of tomcat in spring boot?](#q-11)
- [12. Can we override or replace the Embedded tomcat server in Spring Boot?](#q-12)
- [13. Can we disable the default web server in the Spring boot application?](#q-13)
- [14. Describe the flow of HTTPS requests through the Spring Boot application?](#q-14)
- [15. What is the use of Profiles in spring boot?](#q-15)
- [16. What is Spring Actuator? What are its advantages?](#q-16)
- [17. Where do we define properties in the Spring Boot application?](#q-17)
- [18. What is an IOC container?](#q-18)
<a id="q-1"></a>
## 1. Question
What are the advantages of using Spring Boot?

### Answer
For "What are the advantages of using Spring Boot?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What are the Spring Boot key components?

### Answer
For "What are the Spring Boot key components?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
Why Spring Boot over Spring?

### Answer
For "Why Spring Boot over Spring?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
What is the purpose of using @ComponentScan in the class files?

### Answer
For "What is the purpose of using @ComponentScan in the class files?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
What are starter dependencies?

### Answer
For "What are starter dependencies?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
What is Spring Initializer?

### Answer
For "What is Spring Initializer?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-7"></a>
## 7. Question
What is Spring Boot CLI and what are its benefits?

### Answer
For "What is Spring Boot CLI and what are its benefits?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-8"></a>
## 8. Question
What are the most common Spring Boot CLI commands?

### Answer
For "What are the most common Spring Boot CLI commands?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-9"></a>
## 9. Question
Can we create a non-web application in Spring Boot?

### Answer
For "Can we create a non-web application in Spring Boot?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-10"></a>
## 10. Question
Is it possible to change the port of the embedded Tomcat server in Spring Boot?

### Answer
For "Is it possible to change the port of the embedded Tomcat server in Spring Boot?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-11"></a>
## 11. Question
What is the default port of tomcat in spring boot?

### Answer
For "What is the default port of tomcat in spring boot?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-12"></a>
## 12. Question
Can we override or replace the Embedded tomcat server in Spring Boot?

### Answer
For "Can we override or replace the Embedded tomcat server in Spring Boot?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-13"></a>
## 13. Question
Can we disable the default web server in the Spring boot application?

### Answer
For "Can we disable the default web server in the Spring boot application?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-14"></a>
## 14. Question
Describe the flow of HTTPS requests through the Spring Boot application?

### Answer
For "Describe the flow of HTTPS requests through the Spring Boot application?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-15"></a>
## 15. Question
What is the use of Profiles in spring boot?

### Answer
For "What is the use of Profiles in spring boot?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-16"></a>
## 16. Question
What is Spring Actuator? What are its advantages?

### Answer
Spring Boot Actuator provides production-ready monitoring endpoints such as `/health`, `/metrics`, and `/info`. It improves observability, but sensitive endpoints should be secured and exposed selectively.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-17"></a>
## 17. Question
Where do we define properties in the Spring Boot application?

### Answer
For "Where do we define properties in the Spring Boot application?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-18"></a>
## 18. Question
What is an IOC container?

### Answer
For "What is an IOC container?", explain how Spring Boot auto-configuration, dependency injection, and externalized configuration participate in the flow. Include one production consideration such as profiles, security, or observability.

### Code Snippet
```java
@RestController // REST controller that returns JSON/text directly
@RequestMapping("/api/users")
public class UserController {

    @GetMapping("/{id}") // Handles HTTP GET /api/users/{id}
    public String getUser(@PathVariable Long id) {
        return "User-" + id; // demo response payload
    }
}
```

### Keywords/Tags
- spring-boot
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
