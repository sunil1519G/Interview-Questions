# Dbms Interview Questions (Basic)

Source PDF: `DBMS Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What is meant by a database?](#q-1)
- [2. What is meant by ACID properties in DBMS?](#q-2)
- [3. Are NULL values in a database the same as that of blank space or zero?](#q-3)
- [4. What is meant by Data Warehousing?](#q-4)
- [5. What is meant by normalization and denormalization?](#q-5)
- [6. What is meant by an entity-relationship (E-R) model?](#q-6)
<a id="q-1"></a>
## 1. Question
What is meant by a database?

### Answer
A database is a structured collection of related data stored electronically for efficient retrieval and updates. A DBMS manages this data with security, concurrency control, constraints, backup, and recovery.

### Code Snippet
```sql
-- Basic table definition in a relational database
CREATE TABLE users (
  id BIGINT PRIMARY KEY,
  email VARCHAR(255) UNIQUE NOT NULL
);
```

### Keywords/Tags
- dbms
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
What is meant by ACID properties in DBMS?

### Answer
ACID stands for Atomicity, Consistency, Isolation, and Durability. These properties ensure transactions remain reliable even under failures or concurrent operations.

### Code Snippet
```sql
-- Transfer money atomically between two accounts
BEGIN;
UPDATE accounts SET balance = balance - 1000 WHERE id = 10; -- debit sender
UPDATE accounts SET balance = balance + 1000 WHERE id = 20; -- credit receiver
COMMIT; -- both updates persist together
```

### Keywords/Tags
- dbms
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
Are NULL values in a database the same as that of blank space or zero?

### Answer
`NULL` means unknown/missing data, not empty string and not zero. Queries must use `IS NULL`/`IS NOT NULL`, because equality operators do not match `NULL` as regular values.

### Code Snippet
```sql
-- Correct NULL handling in SQL
SELECT id, name
FROM employees
WHERE manager_id IS NULL; -- finds rows with missing manager reference
```

### Keywords/Tags
- dbms
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
What is meant by Data Warehousing?

### Answer
Data warehousing is the process of consolidating historical data from multiple sources into a central analytical store. It is optimized for reporting/OLAP workloads (read-heavy), unlike OLTP systems optimized for transactional writes.

### Code Snippet
```sql
-- Typical warehouse aggregate query (read-optimized)
SELECT date_key, SUM(total_amount) AS revenue
FROM fact_sales
GROUP BY date_key
ORDER BY date_key;
```

### Keywords/Tags
- dbms
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
What is meant by normalization and denormalization?

### Answer
Normalization decomposes tables to reduce redundancy and anomalies; denormalization introduces controlled redundancy to speed up read queries. Teams typically normalize OLTP schemas and selectively denormalize for analytics/performance.

### Code Snippet
```sql
-- Normalized model: separate customer and order data
CREATE TABLE customers (id BIGINT PRIMARY KEY, name VARCHAR(100));
CREATE TABLE orders (
  id BIGINT PRIMARY KEY,
  customer_id BIGINT REFERENCES customers(id), -- avoids name duplication
  amount DECIMAL(12,2)
);
```

### Keywords/Tags
- dbms
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-6"></a>
## 6. Question
What is meant by an entity-relationship (E-R) model?

### Answer
An ER model is a high-level data model showing entities, attributes, and relationships (1:1, 1:N, M:N). It helps translate business rules into relational schema design before creating tables.

### Code Snippet
```sql
-- ER relation mapped to tables: Department 1:N Employee
CREATE TABLE departments (id BIGINT PRIMARY KEY, name VARCHAR(100));
CREATE TABLE employees (
  id BIGINT PRIMARY KEY,
  dept_id BIGINT REFERENCES departments(id), -- relationship link
  name VARCHAR(100)
);
```

### Keywords/Tags
- dbms
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
