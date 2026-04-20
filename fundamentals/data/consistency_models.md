# Consistency Models

How up-to-date data is across a distributed system.

---

## Types

**Strong Consistency**
All users see the latest data, always.
- Accurate
- Higher latency

**Eventual Consistency**
Data syncs across nodes over time, not instantly.
- High availability, low latency
- Temporary stale data

**Causal Consistency**
Maintains cause-effect order between operations.
- Middle ground between strong and eventual

---

## When to Use

| Model | Use Case |
|---|---|
| Strong | Banking, payments |
| Eventual | Social media feeds, notifications |
| Causal | Collaborative tools, chat apps |

Used by WhatsApp, Instagram.

---

## Trade-offs

| Factor | Strong | Eventual |
|---|---|---|
| Accuracy | High | Temporary stale |
| Latency | High | Low |
| Availability | Lower | High |

---

**Pick based on what your system can't afford to lose — accuracy or availability.**
