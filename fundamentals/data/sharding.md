# Database Sharding

Splitting a database into smaller parts (shards) across multiple servers.

---

## Why Sharding?

- Handle large datasets
- Improve write scalability
- Distribute load

---

## Sharding Strategies

**Range-based** — Data split by ranges (e.g., user IDs 1–10k on shard 1, 10k–20k on shard 2)

**Hash-based** — Hash function decides which shard the data goes to

**Directory-based** — Lookup table maps data to its shard

---

## Challenges

- Hotspots — uneven load if data isn't distributed well
- Rebalancing — adding new shards is painful
- Cross-shard queries — joins become complex and slow

---

## Trade-offs

| Factor | Details |
|---|---|
| Scalability | High |
| Performance | Better under load |
| Architecture | Complex |
| Joins | Difficult across shards |

---

## When to Use

Large-scale systems with massive data and high write load.

Used by Uber, Instagram.

---

**Sharding = horizontal scaling for databases. Trade-off is complexity.**
