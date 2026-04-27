# WhatsApp System Design (HLD)

---

## Requirements

**Functional**
- One-to-one and group messaging
- Message delivery status (sent, delivered, read)
- Media sharing (images, videos)
- Online/offline status

**Non-Functional**
- Latency < 100ms
- Availability 99.99%
- Scales to millions of concurrent users
- No message loss, data durability

---

## High-Level Architecture

```
Client → Load Balancer → WebSocket Servers → Message Service
                                                    ↓
                                             Message Queue
                                                    ↓
                                               Database
                                                    ↓
                                                 Cache
```

---

## Core Components

**WebSocket Servers** — Persistent connections with clients. Enables real-time, avoids repeated HTTP overhead.

**Message Service** — Validates sender/receiver, processes message, pushes to queue.

**Message Queue** — Decouples components. Handles traffic spikes. Ensures no message is lost.

**Database (NoSQL)** — Stores messages. High write throughput. Keyed by userID.

**Cache** — Stores recent chats. Cuts down DB reads.

**Load Balancer** — Distributes traffic. Keeps system available.

---

## Data Flow

```
User A sends message via WebSocket
→ Hits WebSocket server
→ Forwarded to Message Service
→ Stored in DB
→ Pushed to Message Queue
→ User B online  → delivered instantly via WebSocket
→ User B offline → stored in queue, delivered on reconnect
```

---

## Key Design Decisions

**Why WebSockets?**
Persistent connection = low latency. HTTP polling doesn't work at this scale.

**Why Message Queue?**
Handles spikes. If delivery fails, message stays in queue until delivered.

**Why NoSQL?**
High write scalability. Flexible schema. SQL joins don't fit chat data well.

---

## Scaling Strategy

- Horizontal scaling on WebSocket servers
- Partition users across servers
- Shard DB by user ID
- Replication for availability
- CDN for media

---

## Bottlenecks & Solutions

| Bottleneck | Solution |
|---|---|
| High write load | Sharding + NoSQL |
| Connection handling | Distributed WebSocket servers |
| Message delivery delay | Queue-based async processing |

---

## Trade-offs

| Decision | Benefit | Drawback |
|---|---|---|
| WebSockets | Real-time | Complex connection management |
| NoSQL | Scalable | Weak consistency |
| Async Processing | Better performance | Eventual consistency |

---

## Improvements

- End-to-end encryption
- Push notifications for offline users
- Multi-device sync
- Message ordering guarantees
- Read receipts optimization

---

**Core stack — WebSockets for real-time, queues for reliability, NoSQL for scale. Hard part is balancing latency, consistency, and availability together.**
