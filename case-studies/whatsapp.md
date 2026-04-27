# WhatsApp System Design

---

## Requirements

**Functional**
- One-to-one and group chat
- Message delivery status (sent, delivered, read)
- Offline message delivery

**Non-Functional**
- High availability
- Low latency (real-time)
- Scales to millions of users
- No message loss

---

## High-Level Architecture

---

## Core Components

**Client** — Mobile/Web app. Sends and receives via WebSocket.

**Load Balancer** — Distributes traffic across app servers.

**App Servers** — Handle messaging logic, manage WebSocket connections.

**Message Queue** — Holds messages temporarily. Ensures delivery even when user is offline.

**Database** — Stores chat history. NoSQL preferred for scale.

**Cache** — Stores recent chats. Reduces DB hits.

---

## Data Flow

---

## Scaling Strategy

- Horizontal scaling on app servers
- Database sharded by user ID
- CDN for media delivery
- Cache for frequent reads

---

## Bottlenecks

- High write load on database
- Network latency for real-time delivery
- Message queue backlog under heavy load

---

## Trade-offs

| Factor | Choice |
|---|---|
| Consistency vs Availability | Availability first |
| Latency vs Reliability | Balance both |
| Storage vs Performance | Cache heavy reads |

---

**Real-time messaging at scale = WebSockets + message queues + horizontal scaling. Availability over consistency.**
