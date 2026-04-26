# Spring Boot Interview Questions (Intermediate)

Source PDF: `Springboot Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What is the starter dependency of the Spring boot module?](#q-1)
- [2. How does Spring Boot works?](#q-2)
- [3. What does the @SpringBootApplication annotation do internally?](#q-3)
- [4. How does a spring boot application get started?](#q-4)
- [5. What Are the Basic Annotations that Spring Boot Offers?](#q-5)
- [6. What is Spring Boot dependency management?](#q-6)
- [7. How to disable a specific auto-configuration class?](#q-7)
- [8. Explain @RestController annotation in Sprint boot?](#q-8)
- [9. What is the difference between RequestMapping and GetMapping?](#q-9)
- [10. How to enable Actuator in Spring boot application?](#q-10)
- [11. How to get the list of all the beans in your Spring boot application?](#q-11)
- [12. How to check the environment properties in your Spring boot application?](#q-12)
- [13. How to enable debugging log in the spring boot application?](#q-13)
- [14. What is dependency Injection?](#q-14)
- [15. How do you create a REST API endpoint in Spring Boot?](#q-15)
- [16. What are common data access approaches in Spring Boot?](#q-16)
<a id="q-1"></a>
## 1. Question
What is the starter dependency of the Spring boot module?

### Answer
Spring Boot starter dependencies are curated dependency sets (for example `spring-boot-starter-web`) that include compatible libraries for a specific use case. They simplify setup and avoid manually managing many transitive versions.

### Code Snippet
```xml
<!-- Starter pulls curated web dependencies (Spring MVC, Jackson, validation, etc.) -->
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
How does Spring Boot works?

### Answer
Spring Boot starts by creating an application context, scanning components, and applying auto-configuration based on classpath and properties. For web apps, it also boots an embedded server (Tomcat/Jetty/Undertow) so the app runs as a standalone process.

### Code Snippet
```java
@SpringBootApplication // entry-point annotation
public class App {
    public static void main(String[] args) {
        SpringApplication.run(App.class, args); // bootstraps Spring context + embedded server
    }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
What does the @SpringBootApplication annotation do internally?

### Answer
`@SpringBootApplication` combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`. It marks the bootstrap class, enables auto-config for detected dependencies, and scans beans from its package downward.

### Code Snippet
```java
@SpringBootApplication // entry-point annotation
public class App {
    public static void main(String[] args) {
        SpringApplication.run(App.class, args); // bootstraps Spring context + embedded server
    }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
How does a spring boot application get started?

### Answer
A Spring Boot app starts from `SpringApplication.run(...)`, which builds the environment, initializes the IoC container, loads beans, applies auto-configuration, and starts the embedded web server if needed.

### Code Snippet
```java
@SpringBootApplication // entry-point annotation
public class App {
    public static void main(String[] args) {
        SpringApplication.run(App.class, args); // bootstraps Spring context + embedded server
    }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
What Are the Basic Annotations that Spring Boot Offers?

### Answer
Common Spring Boot annotations include `@SpringBootApplication`, `@RestController`, `@RequestMapping/@GetMapping`, `@Service`, `@Repository`, `@Component`, and `@Configuration`. They declare application entry, web endpoints, service layers, and bean configuration.

### Code Snippet
```java
@Service // service-layer bean
class UserService { }

@RestController // web endpoint bean
@RequestMapping("/api/users")
class UserController {
    private final UserService userService; // injected dependency
    UserController(UserService userService) { this.userService = userService; }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
What is Spring Boot dependency management?

### Answer
Spring Boot dependency management is primarily driven by the Spring Boot BOM, which pins compatible library versions. Using Boot parent/BOM lets you omit explicit versions for many dependencies and reduces version conflict risk.

### Code Snippet
```xml
<!-- Import Spring Boot BOM for compatible versions -->
<dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-dependencies</artifactId>
      <version>3.3.0</version>
      <type>pom</type>
      <scope>import</scope>
    </dependency>
  </dependencies>
</dependencyManagement>
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-7"></a>
## 7. Question
How to disable a specific auto-configuration class?

### Answer
You can disable specific auto-configuration using `exclude` in `@SpringBootApplication` or `spring.autoconfigure.exclude` in properties. This is useful when custom/manual configuration should replace Boot defaults.

### Code Snippet
```java
@SpringBootApplication(
    exclude = DataSourceAutoConfiguration.class // disable default datasource auto-config
)
public class App { }
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-8"></a>
## 8. Question
Explain @RestController annotation in Sprint boot?

### Answer
`@RestController` marks a class as a REST endpoint where method return values are written directly to HTTP response body (usually JSON). It is shorthand for `@Controller` + `@ResponseBody`.

### Code Snippet
```java
@RestController // returns data directly in HTTP response body
@RequestMapping("/api/users")
class UserController {
    @GetMapping("/{id}") // maps GET /api/users/{id}
    UserDto get(@PathVariable Long id) {
        return new UserDto(id, "Sunil"); // serialized to JSON
    }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-9"></a>
## 9. Question
What is the difference between RequestMapping and GetMapping?

### Answer
`@RequestMapping` is a general-purpose mapping annotation that can match multiple HTTP methods. `@GetMapping` is a specialized shortcut for HTTP GET, improving readability and intent clarity.

### Code Snippet
```java
@RestController
@RequestMapping("/api/orders") // class-level common path
class OrderController {
    @GetMapping("/{id}") // GET-specific shortcut mapping
    String find(@PathVariable Long id) { return "order-" + id; }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-10"></a>
## 10. Question
How to enable Actuator in Spring boot application?

### Answer
Add `spring-boot-starter-actuator` and expose required endpoints via configuration (for example health, info, metrics). In production, secure sensitive endpoints and limit exposure to trusted networks/roles.

### Code Snippet
```properties
# Enable selected actuator endpoints
management.endpoints.web.exposure.include=health,info,metrics,beans,env
management.endpoint.health.show-details=when_authorized
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-11"></a>
## 11. Question
How to get the list of all the beans in your Spring boot application?

### Answer
You can fetch all bean names from `ApplicationContext` (or expose `/actuator/beans` when actuator is enabled). This helps inspect runtime wiring and troubleshoot unexpected bean resolution.

### Code Snippet
```java
@Component
class BeanInspector {
    BeanInspector(ApplicationContext ctx) {
        String[] beans = ctx.getBeanDefinitionNames(); // list registered beans
        System.out.println("Bean count: " + beans.length);
    }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-12"></a>
## 12. Question
How to check the environment properties in your Spring boot application?

### Answer
You can inspect properties using Spring `Environment` API in code or `/actuator/env` endpoint (if enabled). This helps verify effective config after profile/property-source resolution.

### Code Snippet
```java
@Component
class EnvReader {
    EnvReader(Environment env) {
        String port = env.getProperty("server.port", "8080"); // read effective config
        System.out.println("Server port: " + port);
    }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-13"></a>
## 13. Question
How to enable debugging log in the spring boot application?

### Answer
Enable debug mode with `debug=true` in configuration or `--debug` at startup to see auto-configuration reports. You can also set package-level log levels (for example `logging.level.org.springframework=DEBUG`).

### Code Snippet
```properties
# Enable detailed framework debugging logs
logging.level.org.springframework=DEBUG
logging.level.org.hibernate.SQL=DEBUG
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-14"></a>
## 14. Question
What is dependency Injection?

### Answer
Dependency Injection means object dependencies are provided by the container rather than created manually inside classes. In Spring Boot, constructor injection is preferred for immutability, testability, and explicit dependencies.

### Code Snippet
```java
@Service
class PaymentService { }

@RestController
class PaymentController {
    private final PaymentService paymentService;

    PaymentController(PaymentService paymentService) { // constructor injection
        this.paymentService = paymentService;
    }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-15"></a>
## 15. Question
How do you create a REST API endpoint in Spring Boot?

### Answer
Define a `@RestController`, map routes with `@RequestMapping`/`@GetMapping`/`@PostMapping`, and return DTO/domain responses. Spring handles HTTP mapping and JSON serialization automatically via Jackson.

### Code Snippet
```java
@RestController // returns data directly in HTTP response body
@RequestMapping("/api/users")
class UserController {
    @GetMapping("/{id}") // maps GET /api/users/{id}
    UserDto get(@PathVariable Long id) {
        return new UserDto(id, "Sunil"); // serialized to JSON
    }
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-16"></a>
## 16. Question
What are common data access approaches in Spring Boot?

### Answer
Common Spring Boot data access approaches include Spring Data JPA repositories, JDBC/JdbcTemplate, and R2DBC for reactive databases. Choice depends on query complexity, performance needs, and transaction requirements.

### Code Snippet
```java
@Repository
interface UserRepository extends JpaRepository<User, Long> { // Spring Data JPA approach
    Optional<User> findByEmail(String email);
}
```

### Keywords/Tags
- spring-boot
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
