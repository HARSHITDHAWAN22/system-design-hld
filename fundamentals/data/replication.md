# Database Replication

Copying data from one database server to multiple servers.

---

## Leader-Follower (Master-Slave)

One leader takes all writes. Followers handle reads.


---

## Replication Modes

**Synchronous**
Data written to all replicas before confirming success.
- Strong consistency
- High latency

**Asynchronous**
Leader confirms immediately. Followers catch up later.
- Fast writes
- Eventual consistency, possible data loss

---

## When to Use

- Read-heavy systems
- Systems that need high availability

Used by Instagram, Netflix.

---

## Trade-offs

| Factor | Synchronous | Asynchronous |
|---|---|---|
| Consistency | Strong | Eventual |
| Write Speed | Slow | Fast |
| Data Safety | High | Risk of loss |
| Latency | High | Low |

---

**Replication = better reads + availability. Trade-off is always consistency vs speed.**
