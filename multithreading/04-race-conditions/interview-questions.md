# Interview Questions – Multithreading (Lesson 4)
---

## Q1. What is a race condition?
**Answer:**
A race condition occurs when multiple threads access shared data concurrently and at least one modifies it, causing results to depend on timing.

---

## Q2. Why is `count++` not thread-safe?
**Answer:**
Because it is not atomic. It involves read, modify, and write steps that can interleave between threads.

---

## Q3. What is a timing-dependent bug?
**Answer:**
A bug whose occurrence depends on thread scheduling and execution order.

---

## Q4. Why are race conditions hard to reproduce?
**Answer:**
Because thread scheduling is non-deterministic and depends on OS and JVM timing.

---

## Q5. Is read-only access to shared data safe?
**Answer:**
Yes. Race conditions require at least one write operation.

---

## Q6. What are the consequences of race conditions?
**Answer:**
Lost updates, inconsistent data, incorrect results, and unpredictable behavior.

---

## Q7. Does Java automatically prevent race conditions?
**Answer:**
No. Java allows concurrent access by default; synchronization must be applied explicitly.

---

## Common Interview Traps & Pitfalls

❌ Saying primitive operations are thread-safe  
❌ Assuming `++` is atomic  
❌ Believing Java handles concurrency automatically  
❌ Ignoring timing and scheduling effects  
❌ Thinking race conditions always reproduce  

---

## One Interview-Safe Explanation

> “Race conditions occur due to unsynchronized access to shared mutable state. Operations like increment are not atomic, so results depend on execution timing.”

---
