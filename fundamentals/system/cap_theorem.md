# CAP Theorem

A distributed system can guarantee only 2 out of 3:

- **C** — Consistency
- **A** — Availability
- **P** — Partition Tolerance

---

## What Each Means

**Consistency** — All nodes see the same data at the same time

**Availability** — Every request gets a response, always

**Partition Tolerance** — System keeps working despite network failures

---

## Combinations

**CP (Consistency + Partition Tolerance)**
Drops availability when partition occurs.
- Banking, payment systems

**AP (Availability + Partition Tolerance)**
Drops strong consistency, stays up always.
- Social media, feeds, notifications

---

## Real Insight

Partition tolerance is non-negotiable in real distributed systems. Network failures will happen.

So the real trade-off is always:

