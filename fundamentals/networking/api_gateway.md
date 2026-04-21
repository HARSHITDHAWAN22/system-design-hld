# API Gateway

Single entry point for all client requests in a system.

---

## What It Does

- Routes requests to correct service
- Handles authentication
- Rate limiting
- Logging and monitoring

---

## Why Use It

- Client talks to one place, not multiple services
- Internal architecture stays hidden
- Centralized control over security and traffic

---

## Trade-offs

| Factor | Details |
|---|---|
| Architecture | Cleaner |
| Security | Centralized |
| Single Point of Failure | Risk if gateway goes down |
| Latency | Slight increase |

---

**API Gateway = one door for all requests. Trade-off is it becomes a critical failure point.**
