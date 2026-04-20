# SQL vs NoSQL

---

## Overview

| Feature | SQL | NoSQL |
|---|---|---|
| Structure | Tables | JSON, key-value, document |
| Schema | Fixed | Dynamic |
| Scaling | Vertical | Horizontal |
| Consistency | Strong | Eventual |

---

## SQL

Examples — MySQL, PostgreSQL

Use when:
- Data is structured and relational
- Need ACID transactions
- Complex queries and joins

---

## NoSQL

Types — Key-Value, Document, Column, Graph

Use when:
- Large-scale or unstructured data
- Schema changes frequently
- Need high throughput

---

## Real-World Usage

- Instagram → NoSQL
- Uber → SQL + NoSQL both

---

## Trade-offs

| Factor | SQL | NoSQL |
|---|---|---|
| Consistency | Strong | Eventual |
| Scalability | Limited | High |
| Schema | Rigid | Flexible |
| Transactions | ACID | Limited |

---

**SQL = structure and reliability. NoSQL = scale and flexibility. Most large systems use both.**
