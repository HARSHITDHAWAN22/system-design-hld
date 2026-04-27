# Instagram System Design (HLD)

---

## Requirements

**Functional**
- Upload posts (images/videos)
- Follow/unfollow users
- Like and comment
- Generate user feed
- View profiles

**Non-Functional**
- Low latency feed loading
- High availability
- Scales to millions of users
- High read throughput
- Efficient media storage

---

## High-Level Architecture

```
Client → Load Balancer → API Servers
                              ↓
                         Feed Service
                              ↓
                Cache → Database → Object Storage
```

---

## Core Components

**API Servers** — Handle requests, authentication, routing.

**Feed Service** — Core of the system. Generates what user sees on home screen.

**Database (NoSQL)** — Stores users, posts, relationships. Sharded by user ID.

**Object Storage** — Stores images and videos. Served via CDN.

**Cache** — Stores precomputed feeds. Cuts DB reads drastically.

---

## Feed Generation

**Fan-out on Write**
When user posts → immediately push to all followers' feeds.
- Fast read
- Expensive for celebrities with millions of followers

**Fan-out on Read**
Generate feed when user opens app.
- Low write cost
- Slower read

**Hybrid (used in real systems)**
- Normal users → fan-out on write
- Celebrities → fan-out on read

---

## Data Flow (Post Upload)

```
User uploads image
→ Stored in object storage
→ Metadata saved in DB
→ Feed service updates followers' feeds
→ Cache updated
→ CDN serves media
```

---

## Scaling Strategy

- CDN for media delivery
- Aggressive feed caching
- DB partitioned by user ID
- Async processing for feed updates

---

## Bottlenecks & Solutions

| Bottleneck | Solution |
|---|---|
| Feed generation at scale | Hybrid fan-out + caching |
| Media storage | Object storage + CDN |
| High read traffic | Cache everything |

---

## Trade-offs

| Decision | Benefit | Drawback |
|---|---|---|
| Fan-out on write | Fast reads | Heavy writes |
| Fan-out on read | Light writes | Slow reads |
| Caching | Fast response | Stale data |

---

## Improvements

- ML-based feed ranking
- Stories and Reels (video streaming)
- Content moderation pipeline
- Notification service

---

**Core challenge — feed generation at scale. Hybrid fan-out + aggressive caching is the answer. Read-heavy system, so cache is everything.**
