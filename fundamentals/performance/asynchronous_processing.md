# Asynchronous Processing

## What is Async Processing?

Tasks are handled in the background instead of blocking the main request. The user doesn’t have to wait for everything to finish.

---

## How It Works

Client → Queue → Worker → Processing

---

## Benefits

- Faster response to user  
- Better scalability  
- Good for heavy or long-running tasks  

---

## Trade-offs

- More system complexity  
- Eventual consistency (results may not be immediate)  
- Debugging becomes harder  

---

## Use Cases

- Notifications  
- Email sending  
- Video processing  

Used in real systems like:
- Uber  
- Netflix  

---

## Summary

Async processing improves performance by moving heavy work to background workers, keeping the system fast and responsive.
