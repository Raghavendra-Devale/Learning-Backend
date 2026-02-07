# Multithreading – Lesson 6  
## Deadlock, Livelock & Starvation

These notes explain common concurrency failure scenarios in Java and how they differ. These topics are frequently asked in interviews to test system-level understanding.

---

## 1. Deadlock

A deadlock occurs when two or more threads are permanently blocked, each waiting for a resource held by another thread.

No thread can proceed and the program appears stuck.

---

## 2. Deadlock Scenario (Conceptual)

- Thread A holds Lock 1 and waits for Lock 2
- Thread B holds Lock 2 and waits for Lock 1

This creates a circular dependency where no thread can continue.

---

## 3. Conditions Required for Deadlock

Deadlock occurs only if all of the following are true:
1. Mutual exclusion
2. Hold and wait
3. No preemption
4. Circular wait

Circular wait is the most critical condition.

---

## 4. Livelock

A livelock occurs when threads are not blocked but still make no progress.

Characteristics:
- Threads keep running
- CPU is active
- Threads keep reacting to each other
- No useful work is completed

---

## 5. Starvation

Starvation occurs when a thread never gets CPU time or lock access.

Causes:
- Unfair scheduling
- High-priority threads dominating
- Long synchronized sections

Thread remains alive but never executes.

---

## 6. Key Differences

- Deadlock → threads blocked, no progress
- Livelock → threads running, no progress
- Starvation → thread waits indefinitely while others progress

---

## 7. synchronized and Deadlocks

`synchronized`:
- Prevents race conditions
- Ensures mutual exclusion
- Does NOT prevent deadlocks
- Does NOT guarantee fairness

Incorrect locking design can still lead to deadlock.

---

## 8. Preventing Deadlocks (Design-Level)

Deadlocks are prevented by design, not fixed at runtime:
- Consistent lock ordering
- Avoid nested locks
- Minimize lock scope
- Use higher-level concurrency utilities

---

## 9. Backend Relevance

Deadlocks commonly occur in:
- Nested synchronized blocks
- Database transactions
- Resource pools
- Multi-lock systems

Understanding these concepts helps in debugging production issues.

---

## 10. Interview-Safe Summary

> “Deadlock occurs due to circular lock dependencies, livelock occurs when threads actively avoid progress, and starvation occurs due to unfair scheduling.”

---
