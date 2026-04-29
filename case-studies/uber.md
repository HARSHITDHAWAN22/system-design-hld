# Uber System Design (HLD)

---

## Requirements

**Functional**
- Request a ride
- Match rider with driver
- Real-time ride tracking
- Complete ride and payment

**Non-Functional**
- Low latency matching
- High availability
- Scales to millions of concurrent rides

---

## High-Level Architecture

```
Client → Load Balancer → API Servers
                              ↓
                     Matching Service → Ride Service
                              ↓
                           Database
```

---

## Core Components

**API Servers** — Handle all client requests, authentication, routing.

**Matching Service** — Finds nearest available driver. Core of the system.

**Ride Service** — Manages ride lifecycle — start, track, complete.

**Database** — Stores users, drivers, rides, payments.

---

## Data Flow

```
Rider requests ride
→ API server receives request
→ Matching service finds nearest driver
→ Driver accepts → Ride created
→ Real-time tracking starts
→ Ride completes → Payment processed
```

---

## Scaling Strategy

- Geo-sharding — partition data by location
- WebSockets for real-time driver tracking
- Cache driver locations (updated every few seconds)
- Horizontal scaling on matching service

---

## Bottlenecks & Solutions

| Bottleneck | Solution |
|---|---|
| Driver location updates | Cache + WebSockets |
| Matching at scale | Geo-indexed search |
| Payment processing | Async, separate service |

---

## Trade-offs

| Decision | Benefit | Drawback |
|---|---|---|
| Real-time tracking | Accurate location | High write load |
| Geo-sharding | Fast location queries | Complex rebalancing |
| Async payments | Non-blocking | Slight delay |

---

**Core challenge — real-time matching and tracking at scale. Geo-indexing + WebSockets + caching is the backbone.**


## Real-Time Location Tracking

Drivers send location updates every few seconds → stored in cache (not DB).

- In-memory storage for fast lookup
- DB write would be too slow at this frequency

```
Driver app → Location update → Cache (every 3-5s)
```

---

## Driver-Rider Matching

Uses geospatial indexing (GeoHash) to find nearby drivers fast.

```
Rider requests ride
→ System finds nearby drivers via GeoHash
→ Sends request to closest drivers
→ First driver to accept = matched
→ Ride starts
```

**Why GeoHash?**
Converts location into a string. Nearby locations share same prefix. Fast range queries without scanning entire DB.
