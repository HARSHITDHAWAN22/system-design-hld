# Database Scaling

More users = more reads, more writes, higher latency. Database becomes the bottleneck.

Two ways to handle it.

---

## Vertical Scaling (Scale Up)

Better CPU, more RAM, bigger disk. Same machine, upgraded.

Simple. No architecture changes needed.

But hardware has limits. Gets expensive. Still a single point of failure.

---

## Horizontal Scaling (Scale Out)

Add more machines. Split the load.

Scales well. If one node dies, others handle it.

But now it's a distributed system — sharding, replication, consistency issues. Design gets complex.

---

## When to Use What

Start with vertical. Simple, gets the job done early on.

Move to horizontal when traffic grows or you need high availability.

---

## Trade-offs

| Factor | Vertical | Horizontal |
|---|---|---|
| Complexity | Low | High |
| Scalability | Limited | High |
| Cost | High | Moderate |
| Fault Tolerance | Low | High |

---

**Vertical = simple but limited. Horizontal = complex but scales.**
