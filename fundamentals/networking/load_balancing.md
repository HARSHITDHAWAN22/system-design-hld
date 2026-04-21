---

## Types

**Layer 4 (Transport Layer)** — Routes based on IP + Port. Faster, less intelligent.

**Layer 7 (Application Layer)** — Routes based on HTTP, URL, headers. Smarter routing.

---

## Algorithms

- **Round Robin** — Requests go to each server in order
- **Least Connections** — Routes to server with fewest active connections
- **IP Hash** — Same client always hits same server

---

## Benefits

- Scales traffic across servers
- No single point of failure
- Handles server crashes gracefully

---

## Trade-offs

| Factor | Details |
|---|---|
| Scalability | High |
| Availability | High |
| Latency | Slight increase |
| Cost | Infrastructure overhead |
| Complexity | Increases |

---

## Real-World Usage

Netflix, Uber — load balancers handle millions of requests per second.

---

**Load balancing = traffic distribution + reliability. Trade-off is added infra cost and complexity.**
