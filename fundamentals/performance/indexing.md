# Indexing

## What is Indexing?

A technique used to speed up database queries by avoiding full scans.

---

## How It Works

- Creates a separate data structure (like a pointer/reference)  
- Points to actual data locations  
- Helps in quickly locating required records  

---

## Benefits

- Faster read queries  
- Efficient data retrieval  
- Reduces scan time on large datasets  

---

## Trade-offs

- Takes extra storage  
- Slows down writes (index needs to be updated)  
- Too many indexes can hurt performance  

---

## Summary

Indexing improves read performance significantly, but comes with storage cost and slower write operations.
