# Availability vs Consistency

Core trade-off in distributed systems — you rarely get both fully.

---

## Availability

System responds to every request, even if data isn't the latest.

- No downtime
- May return stale data

Example — Social media feeds, notifications

---

## Consistency

Always returns the latest data, but may delay or reject the request.

- Accurate data
- Higher latency or temporary unavailability

Example — Banking, payments

---

## Real-World Usage

- Instagram → Availability first
- Banking systems → Consistency first

---

## Trade-offs

| Factor | Availability | Consistency |
|---|---|---|
| Response | Always | May delay |
| Data Freshness | Not guaranteed | Guaranteed |
| Latency | Low | High |
| Use Case | Social, feeds | Payments, banking |

---

**Pick based on what hurts more — wrong data or no response.**
