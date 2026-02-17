# Connection Pooling — Notes (0–3 YOE)

---

## What Problem Does It Solve?

Creating DB connections is expensive.

Connection pooling reuses connections instead of creating new ones.

---

## Working Principle

- Pool creates connections at startup
- Application borrows connection
- After use, connection returned to pool

---

## Benefits

- Faster performance
- Reduced DB load
- Better scalability
- Controlled resource usage

---

## Key Concepts

Pool Size
- Maximum connections allowed.

Idle Connection
- Ready but unused connection.

Connection Timeout
- Wait time before failure.

Connection Leak
- Connection not returned to pool.

---

## HikariCP

- Default pool in Spring Boot
- High performance
- Lightweight
- Auto-configured

---

## Important Behavior

connection.close() returns connection to pool (not DB close).

---