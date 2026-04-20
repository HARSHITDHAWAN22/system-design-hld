# Fault Tolerance

System keeps working even when components fail.

---

## Why It Matters

Failures are inevitable — server crashes, network drops, hardware dies. System has to handle it without going down.

---

## Techniques

**Replication** — Duplicate data or services across nodes. One dies, others take over.

**Redundancy** — Backup components on standby.

**Failover** — Automatically switch to backup when primary fails.

---

## Trade-offs

| Factor | Details |
|---|---|
| Availability | High |
| Reliability | High |
| Cost | Increases |
| Complexity | Increases |

---

**Fault tolerance = reliability under failure. Trade-off is cost and complexity.**
