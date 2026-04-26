# Junit Interview Questions (Intermediate)

Source PDF: `JUnit Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What are some of the important annotations provided by JUnit?](#q-1)
- [2. What is the importance of @Test annotation?](#q-2)
- [3. What is the importance of @RunWith annotation?](#q-3)
- [4. How does JUnit help in achieving tests isolation?](#q-4)
- [5. How to ignore tests in JUnit?](#q-5)
- [6. What is the purpose of @Before and @Aer annotations in JUnit 4?](#q-6)
- [7. What are Hamcrest Matchers?](#q-7)
- [8. What is the difference between thenReturn and doReturn?](#q-8)
- [9. What is the main difference between @Mock and @InjectMocks?](#q-9)
<a id="q-1"></a>
## 1. Question
What are some of the important annotations provided by JUnit?

### Answer
JUnit provides several key annotations for structuring tests. `@Test` marks a method as a test case. `@Before` and `@After` run before/after each test for setup and teardown. `@BeforeClass` and `@AfterClass` run once before/after all tests. `@Ignore` skips a test. `@RunWith` specifies a custom test runner (e.g., Parameterized for data-driven tests). These annotations enable test isolation, deterministic execution, and maintainable test suites in CI pipelines.

### Code Snippet
```java
public class CalculatorTest {
    private Calculator calculator;
    
    @Before // runs before each @Test method
    public void setUp() {
        calculator = new Calculator(); // initialize fresh instance
    }
    
    @Test // marks method as a test case
    public void testAddition() {
        int result = calculator.add(2, 3); // execute behavior under test
        assertEquals(5, result);           // verify expected outcome
    }
    
    @Test
    @Ignore("Not yet implemented") // skip this test
    public void testDivisionByZero() {
        calculator.divide(5, 0); // test not executed
    }
    
    @After // runs after each @Test method
    public void tearDown() {
        calculator = null; // cleanup if needed
    }
}
```

### Keywords/Tags
- junit
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What is the importance of @Test annotation?

### Answer
The `@Test` annotation marks a method as a test case that JUnit should execute. Without this annotation, JUnit ignores the method during test discovery and execution. Each `@Test` method should test a single behavior (single responsibility), include setup, execution, and assertion phases (AAA pattern), and must be independent so test execution order doesn't matter. This enables parallel test execution and deterministic, fast feedback in CI/CD pipelines.

### Code Snippet
```java
public class PaymentServiceTest {
    private PaymentService service;
    
    @Before
    public void setUp() {
        service = new PaymentService(new MockGateway()); // Arrange
    }
    
    @Test // marks method for test execution
    public void testSuccessfulPayment() {
        // Act: execute the behavior being tested
        PaymentResult result = service.processPayment(100.00, "USD");
        
        // Assert: verify expected outcome
        assertTrue(result.isSuccessful());
        assertEquals(100.00, result.getAmount());
    }
    
    @Test // each @Test method is independent
    public void testPaymentValidation() {
        PaymentResult result = service.processPayment(-50.00, "USD");
        assertFalse(result.isSuccessful());
    }
}
```

### Keywords/Tags
- junit
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
What is the importance of @RunWith annotation?

### Answer
The `@RunWith` annotation specifies a custom test runner to control test execution. By default, JUnit uses BlockJUnit4ClassRunner. Alternative runners like `Parameterized` enable data-driven tests, `SpringRunner` for Spring integration tests, or `MockitoJUnitRunner` for mock auto-injection. This enables advanced patterns without boilerplate.

### Code Snippet
```java
import org.junit.runner.RunWith;
import org.junit.runners.Parameterized;

@RunWith(Parameterized.class) // use parameterized test runner
public class CalculatorParameterizedTest {
    private int input1, input2, expected;
    private Calculator calculator;
    
    public CalculatorParameterizedTest(int input1, int input2, int expected) {
        this.input1 = input1;
        this.input2 = input2;
        this.expected = expected;
    }
    
    @Before
    public void setUp() {
        calculator = new Calculator();
    }
    
    @Parameterized.Parameters(name = "{0} + {1} = {2}")
    public static Collection<Object[]> data() {
        return Arrays.asList(new Object[][] {
            { 2, 3, 5 }, { 0, 5, 5 }, { -1, 1, 0 }
        });
    }
    
    @Test // runs once per parameter set
    public void testAddition() {
        assertEquals(expected, calculator.add(input1, input2));
    }
}
```

### Keywords/Tags
- junit
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
How does JUnit help in achieving tests isolation?

### Answer
Test isolation ensures each test is independent and runs in any order. `@Before`/`@After` create fresh fixtures for each test. Tests shouldn't share state, write to disk, or depend on external services. Mocking dependencies strengthens isolation, enabling parallel execution and preventing cascading failures.

### Code Snippet
```java
public class UserServiceTest {
    private UserService userService;
    private UserRepository mockRepository;
    
    @Before
    public void setUp() {
        mockRepository = mock(UserRepository.class);
        userService = new UserService(mockRepository);
    }
    
    @Test
    public void testCreateUserSuccess() {
        when(mockRepository.save(any())).thenReturn(1);
        
        User newUser = new User("alice", "alice@example.com");
        int userId = userService.create(newUser);
        
        assertEquals(1, userId);
        verify(mockRepository).save(any());
    }
    
    @Test
    public void testCreateUserWithDuplicate() {
        when(mockRepository.save(any())).thenThrow(new DuplicateException());
        
        User newUser = new User("bob", "bob@example.com");
        assertThrows(DuplicateException.class, () -> userService.create(newUser));
    }
    
    @After
    public void tearDown() {
        mockRepository = null;
        userService = null;
    }
}
```

### Keywords/Tags
- junit
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
How to ignore tests in JUnit?

### Answer
The `@Ignore` annotation marks test methods or classes to be skipped. Use with a reason string to document why: `@Ignore("Waiting for API integration")`. Ignoring should be temporary—convert ignored tests to passing tests as soon as possible.

### Code Snippet
```java
public class OrderServiceTest {
    
    @Test
    public void testOrderCreation() {
        Order order = new Order("ORD123", 100.00);
        assertEquals("ORD123", order.getId());
    }
    
    @Test
    @Ignore // test is skipped
    public void testOrderShipping() {
        Order order = new Order("ORD456", 200.00);
        order.ship();
        assertTrue(order.isShipped());
    }
    
    @Test
    @Ignore("Waiting for payment gateway integration")
    public void testPaymentProcessing() {
        Order order = new Order("ORD789", 300.00);
        order.processPayment();
        assertTrue(order.isPaid());
    }
}
```

### Keywords/Tags
- junit
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
What is the purpose of @Before and @After annotations in JUnit 4?

### Answer
`@Before` runs before each `@Test` for setup: initializing objects, opening connections, loading test data. `@After` runs after each `@Test` for teardown: closing connections, cleaning files, resetting state. Together they ensure isolation and deterministic behavior. `@BeforeClass` and `@AfterClass` run once for the entire test class (static methods).

### Code Snippet
```java
public class DatabaseConnectionTest {
    private DatabaseConnection connection;
    
    @Before // runs before each @Test
    public void setUp() throws Exception {
        connection = new DatabaseConnection();
        connection.connect("localhost:5432");
        connection.clearTables();
    }
    
    @Test
    public void testInsertRecord() {
        connection.insert("users", new Record("alice", 30));
        Record retrieved = connection.query("SELECT * FROM users WHERE name='alice'");
        assertEquals("alice", retrieved.getName());
    }
    
    @Test
    public void testUpdateRecord() {
        connection.insert("users", new Record("bob", 25));
        connection.update("users", "bob", new Record("bob", 26));
        Record retrieved = connection.query("SELECT * FROM users WHERE name='bob'");
        assertEquals(26, retrieved.getAge());
    }
    
    @After // runs after each @Test
    public void tearDown() throws Exception {
        connection.clearTables();
        connection.disconnect();
    }
    
    @BeforeClass // runs once before all @Test
    public static void setupClass() {
        System.out.println("Test class initialization");
    }
}
```

### Keywords/Tags
- junit
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-7"></a>
## 7. Question
What are Hamcrest Matchers?

### Answer
Hamcrest provides fluent, readable assertions. Instead of `assertEquals(x, y)`, write `assertThat(x, is(y))` or `assertThat(list, hasItem(item))`. Matchers provide better error messages and composability (combine with `allOf`, `anyOf`, `not`). Makes tests readable and debugging easier.

### Code Snippet
```java
import static org.hamcrest.Matchers.*;
import static org.hamcrest.MatcherAssert.assertThat;

public class HamcrestMatchersTest {
    
    @Test
    public void testStringMatching() {
        String name = "Alice";
        assertThat(name, is("Alice"));
        assertThat(name, startsWith("Al"));
        assertThat(name, containsString("li"));
    }
    
    @Test
    public void testCollectionMatching() {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        assertThat(numbers, hasSize(5));
        assertThat(numbers, hasItem(3));
        assertThat(numbers, everyItem(greaterThan(0)));
    }
    
    @Test
    public void testComposableMatchers() {
        List<String> fruits = Arrays.asList("apple", "banana", "apricot");
        assertThat(fruits, allOf(
            hasSize(3),
            hasItem(startsWith("a")),
            hasItem(containsString("na"))
        ));
    }
}
```

### Keywords/Tags
- junit
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-8"></a>
## 8. Question
What is the difference between thenReturn and doReturn?

### Answer
`when(mock.method(args)).thenReturn(value)` calls the method during setup (fails if method throws). `doReturn(value).when(mock).method(args)` doesn't call the method, safer for exception-throwing methods. Use `doReturn` for void methods or to avoid triggering real logic.

### Code Snippet
```java
import static org.mockito.Mockito.*;

public class MockitoReturnDifferencesTest {
    
    @Test
    public void testThenReturn() {
        UserService mockService = mock(UserService.class);
        when(mockService.getUser("alice")).thenReturn(new User("alice", 30));
        
        User result = mockService.getUser("alice");
        assertEquals("alice", result.getName());
    }
    
    @Test
    public void testDoReturnForExceptions() {
        UserRepository mockRepo = mock(UserRepository.class);
        // thenReturn would FAIL if method throws IOException
        doReturn(new User("bob", 25)).when(mockRepo).findById(1);
        
        User user = mockRepo.findById(1);
        assertEquals("bob", user.getName());
    }
    
    @Test
    public void testDoReturnWithSpies() {
        UserService realService = new UserService();
        UserService spyService = spy(realService);
        
        // Override spy behavior without calling real method
        doReturn(new User("override", 99)).when(spyService).getUser("alice");
        
        User result = spyService.getUser("alice");
        assertEquals("override", result.getName());
    }
}
```

### Keywords/Tags
- junit
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-9"></a>
## 9. Question
What is the main difference between @Mock and @InjectMocks?

### Answer
`@Mock` creates a mock object (test double). `@InjectMocks` creates a real instance and automatically injects `@Mock` fields into it. Use `@Mock` for dependencies, `@InjectMocks` for system under test. Reduces boilerplate and makes dependencies explicit. Requires `MockitoAnnotations.openMocks(this)` or `@ExtendWith(MockitoExtension.class)`.

### Code Snippet
```java
import org.mockito.Mock;
import org.mockito.InjectMocks;
import org.mockito.junit.MockitoJUnitRunner;
import org.junit.runner.RunWith;

@RunWith(MockitoJUnitRunner.class)
public class PaymentServiceTest {
    
    @Mock
    private PaymentGateway mockGateway;
    
    @Mock
    private AuditLogger mockLogger;
    
    @InjectMocks
    private PaymentService paymentService;
    
    @Test
    public void testSuccessfulPayment() {
        when(mockGateway.charge(100.00)).thenReturn(new TransactionId("TXN123"));
        
        TransactionId result = paymentService.processPayment(100.00);
        
        assertEquals("TXN123", result.getId());
        verify(mockGateway).charge(100.00);
        verify(mockLogger).log(contains("payment"));
    }
    
    @Test
    public void testPaymentFailure() {
        when(mockGateway.charge(any())).thenThrow(new NetworkException("timeout"));
        
        assertThrows(PaymentException.class, () -> {
            paymentService.processPayment(500.00);
        });
        
        verify(mockLogger).log(contains("error"));
    }
}
```

### Keywords/Tags
- junit
- intermediate

### Difficulty
- intermediate

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
