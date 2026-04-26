# System Design Interview Questions (Advanced)

Source PDF: `System Design Interview Questions.pdf`

Curated from source questions with technical corrections and interview-focused wording.

## Question Index

- [1. What do you understand by Latency, throughput, and availability of a system?](#q-1)
- [2. How is sharding different from partitioning?](#q-2)
- [3. How is performance and scalability related to each other?](#q-3)
- [4. What are the various Consistency patterns available in system design?](#q-4)
- [5. What are some of the design issues in distributed systems?](#q-5)
<a id="q-1"></a>
## 1. Question
What do you understand by Latency, throughput, and availability of a system?

### Answer
For "What do you understand by Latency, throughput, and availability of a system?", start with requirements and constraints, then cover components, data flow, scaling strategy, and failure handling. Explicitly discuss trade-offs (latency, consistency, complexity, and cost).

### Code Snippet
```text
Client -> API Gateway -> Service -> Cache -> Database
# Route requests through gateway for auth/rate limiting
# Cache hot reads to reduce database latency
```

### Keywords/Tags
- system-design
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-2"></a>
## 2. Question
How is sharding different from partitioning?

### Answer
For "How is sharding different from partitioning?", start with requirements and constraints, then cover components, data flow, scaling strategy, and failure handling. Explicitly discuss trade-offs (latency, consistency, complexity, and cost).

### Code Snippet
```text
Client -> API Gateway -> Service -> Cache -> Database
# Route requests through gateway for auth/rate limiting
# Cache hot reads to reduce database latency
```

### Keywords/Tags
- system-design
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-3"></a>
## 3. Question
How is performance and scalability related to each other?

### Answer
For "How is performance and scalability related to each other?", start with requirements and constraints, then cover components, data flow, scaling strategy, and failure handling. Explicitly discuss trade-offs (latency, consistency, complexity, and cost).

### Code Snippet
```text
Client -> API Gateway -> Service -> Cache -> Database
# Route requests through gateway for auth/rate limiting
# Cache hot reads to reduce database latency
```

### Keywords/Tags
- system-design
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-4"></a>
## 4. Question
What are the various Consistency patterns available in system design?

### Answer
For "What are the various Consistency patterns available in system design?", start with requirements and constraints, then cover components, data flow, scaling strategy, and failure handling. Explicitly discuss trade-offs (latency, consistency, complexity, and cost).

### Code Snippet
```text
Client -> API Gateway -> Service -> Cache -> Database
# Route requests through gateway for auth/rate limiting
# Cache hot reads to reduce database latency
```

### Keywords/Tags
- system-design
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)

<a id="q-5"></a>
## 5. Question
What are some of the design issues in distributed systems?

### Answer
Key challenges: (1) **Network partitions**: servers can't communicate but appear alive to clients (split-brain). (2) **Clock synchronization**: servers have different time, breaks causality assumptions. (3) **Consensus**: getting multiple servers to agree on state is expensive (Raft, Paxos). (4) **Failure detection**: hard to distinguish crashed server from slow network. (5) **Data consistency**: eventual consistency introduces stale reads. (6) **Cascading failures**: one service down brings down dependent services. (7) **Distributed transactions**: ACID properties hard to maintain. (8) **Debugging**: hard to reproduce bugs with async interactions. Mitigations: timeouts, circuit breakers, retry logic with idempotency, monitoring, distributed tracing.

### Code Snippet
```text
1. NETWORK PARTITION (Split-Brain Problem)

Before partition:
Master (Shard 1) <- App -> Replicas (Shard 1)
              ↓
Client traffic routed by load balancer

Partition occurs:
┌─────────────────┐     NETWORK DOWN     ┌──────────────┐
│ Master (Shard 1)│◄──────PARTITION──────►│ Replicas     │
│ Sees 1 replica  │                       │ Lost master  │
│ Can't see others│                       │ Elect new    │
│ Down to 2 nodes │                       │ leader       │
│ Continues writes│                       │              │
└─────────────────┘                       └──────────────┘

       ↓ (OLD Master writes)              ↓ (NEW Master writes)
      [A=100, B=200]                      [A=100, B=250]
     
       ↓ (Partition heals)

DATA CONFLICT! Cannot simply merge.
Mitigation: Use Quorum consensus (need majority)
Partition: Minority side shuts down (prevents writes)


2. CLOCK SKEW (Time Synchronization Issues)

Server A clock: 10:00:00
Server B clock: 09:59:50 (10 seconds behind)

Event order on Server A:
Write X=100 at 10:00:00
Write X=200 at 10:00:01

Event order on Server B:
Receives: Write X=100 at 09:59:50
Receives: Write X=200 at 10:00:01
Local order: Write X=200 BEFORE Write X=100 (WRONG!)

Problem: Distributed transactions assume clock monotonicity
Solution: Use Lamport clocks or vector clocks (logical time)


3. CONSENSUS COMPLEXITY (Raft/Paxos)

Goal: All 5 servers agree on state
Scenario: Server A proposes new value

┌─ Server 1 ──────────────────────┐
│ Receives proposal from A        │
│ Acknowledges                    │
└────────────────────────────────┬┘
                                  │
┌─ Server 2 ──────────────────────┐
│ Receives proposal from A        │
│ Network timeout (no ack)        │
└────────────────────────────────┬┘
                                  │
┌─ Server 3 ──────────────────────┐
│ Receives proposal from A        │
│ Acknowledges                    │
└────────────────────────────────┬┘

Majority (3 out of 5) acknowledges: proposal committed
But Server 2 has no record (must replay log on sync)

Cost: O(N) messages per consensus, ~100-500ms latency


4. FAILURE DETECTION (Crash vs Slow Network)

Is Server X down?
┌─ Server A ────────────────┐
│ Ping Server X at t=1000ms │
│ No response at t=1100ms   │
│ Server X is DOWN?         │
└──────────────────────────┘

Actually: Network is just slow
Server X is alive but packet delayed

Timeout too short: False positives (false suspicion)
Timeout too long: Slow failure detection

Solution: Adaptive timeouts, heartbeats, gossip protocol


5. DATA INCONSISTENCY (Eventual Consistency)

Write A=100 to primary
Async replicate to secondary (100ms lag)

Client 1: Writes A=100 (primary)
Client 2: Reads A immediately (from secondary still has A=50)

Reads stale data!

Mitigation:
- Route writes and immediately-following reads to same replica
- Use version vectors to detect causal order
- Accept inconsistency (social media OK, banking NOT OK)


6. CASCADING FAILURES

┌─ Service A ─────────┐
│ Calls Service B     │
│ 1000 requests/sec   │
└─────────────────────┘
        ↓ (no timeout)
┌─ Service B ─────────┐
│ DOWN (overload)     │
└─────────────────────┘

Service A threads wait indefinitely
Thread pool exhausted
Service A becomes unresponsive
Upstream services timeout to Service A
Entire system cascades down

Mitigation:
- Timeouts on all remote calls
- Bulkheads: isolate resources per service
- Circuit breakers: stop calling dead service
- Rate limiting: protect from thundering herd


7. DISTRIBUTED TRANSACTIONS

Goal: Transfer money from Account A to Account B across databases
┌─ Shard 1 (A) ─────────────────┐
│ Debit A by $100               │
└─────────────────────────────┬─┘
                              │
┌─ Shard 2 (B) ─────────────────┐
│ Credit B by $100              │
│ (Shard 1 crashes here!)       │
└─────────────────────────────┬─┘

Result: Money disappears!

2-Phase Commit (XA):
Phase 1: Prepare (all shards say "yes, can commit")
Phase 2: Commit (all shards execute)
Cost: Blocking, single point of failure

Better: Event sourcing + Saga pattern
Shard 1: Debit A, emit "account.debited" event
Shard 2: Listen, credit B, emit "account.credited" event
Failure: Compensating transactions
Cost: Eventual consistency, increased complexity


8. DEBUGGING DISTRIBUTED SYSTEMS

Monolith: Reproduce bug locally, set breakpoint
Distributed: 
- Bug happens when 3 services interact under load
- Irreproducible in dev environment
- 10ms timing window triggers bug
- Logs scattered across 100 service instances

Solution: Distributed tracing, correlation IDs, comprehensive logging


DESIGN PRINCIPLES FOR RESILIENCE:

1. Timeouts: Fail fast, don't wait indefinitely
2. Retries: Exponential backoff for transient failures
3. Idempotency: Same operation can be retried safely
4. Circuit breakers: Stop cascading failures
5. Monitoring: Detect issues before users
6. Graceful degradation: Serve stale data vs crash
7. Replication: tolerate server failures
8. Sharding: tolerate partition tolerance
```

### Keywords/Tags
- system-design
- advanced

### Difficulty
- advanced

### Related Questions
- Add cross-links to related topic files as content grows.

[Back to Question Index](#question-index)
