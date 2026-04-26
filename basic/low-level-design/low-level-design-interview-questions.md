# Low Level Design Interview Questions (Basic)

Source PDF: `Low Level Design Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. Why LLD is Important?](#q-1)
<a id="q-1"></a>
## 1. Question
Why LLD is Important?

### Answer
For "Why LLD is Important?", explain class responsibilities, interfaces, object interactions, and extensibility points. Mention SOLID-driven trade-offs and how the design remains testable and maintainable.

### Code Snippet
```text
Client -> API Gateway -> Service -> Cache -> Database
# Route requests through gateway for auth/rate limiting
# Cache hot reads to reduce database latency
```

### Keywords/Tags
- low-level-design
- basic

### Difficulty
- basic

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
