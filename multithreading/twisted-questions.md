# 🧠 Multithreading — Twisted & Indirect Interview Questions

This file contains **indirect, scenario-based, and trap questions**
used to test **real concurrency understanding**, not syntax.

Use this before interviews where:
- questions are indirect
- interviewer probes fundamentals through scenarios
- multithreading is used to eliminate candidates

---

## 1️⃣ Thread vs Runnable vs Task (Design Traps)

### Q1. Why is `Runnable` preferred over extending `Thread`?
**Answer:**
Extending `Thread` creates tight coupling and prevents class inheritance.
`Runnable` provides loose coupling and better design flexibility.

---

### Q2. What happens if you call `run()` directly?
**Answer:**
It executes like a normal method on the current thread.
No new thread is created.

---

### Q3. What happens if you call `start()` twice on the same thread?
**Answer:**
`IllegalThreadStateException` is thrown.
A thread can be started only once in its lifetime.

---

## 2️⃣ Thread Lifecycle & State Confusion

### Q4. Is a thread in RUNNABLE state always running?
**Answer:**
No.
RUNNABLE means the thread is ready to run or running,
waiting for CPU scheduling.

---

### Q5. BLOCKED vs WAITING — what’s the real difference?
**Answer:**
- BLOCKED → waiting to acquire a lock
- WAITING → waiting for coordination (`wait()`, `join()`)

---

## 3️⃣ `sleep()` vs `wait()` (Object vs Thread Trap)

### Q6. Where does `sleep()` come from?
**Answer:**
`sleep()` is a static method of `Thread`.

---

### Q7. Where does `wait()` come from?
**Answer:**
`wait()` is a method of `Object`.

---

### Q8. Why must `wait()` be called inside a synchronized block?
**Answer:**
Because `wait()` releases the monitor lock,
which the thread must own before calling it.

---

### Q9. Does `sleep()` release a lock?
**Answer:**
No.
`sleep()` pauses execution but does not release any locks.

---

## 4️⃣ Race Conditions & Visibility Traps

### Q10. Why is `count++` not thread-safe?
**Answer:**
Because it is a compound operation:
read → modify → write.
Multiple threads can interleave these steps.

---

### Q11. Why do race conditions seem random?
**Answer:**
They depend on thread scheduling, CPU timing, and JVM behavior,
making them unpredictable.

---

## 5️⃣ `synchronized` — Deep Traps

### Q12. What exactly does `synchronized` guarantee?
**Answer:**
- Mutual exclusion
- Visibility of shared data

---

### Q13. What object is locked in a synchronized instance method?
**Answer:**
The current object (`this`).

---

### Q14. What is locked in a synchronized static method?
**Answer:**
The `Class` object.

---

### Q15. Why is block-level synchronization preferred?
**Answer:**
It reduces lock scope and improves performance.

---

## 6️⃣ Deadlock, Livelock & Starvation

### Q16. Does `synchronized` prevent deadlocks?
**Answer:**
No.
Poor lock ordering can still cause deadlocks.

---

### Q17. Deadlock vs Livelock?
**Answer:**
- Deadlock → threads are blocked forever
- Livelock → threads keep running but make no progress

---

### Q18. What is starvation?
**Answer:**
A thread never gets CPU or resources due to scheduling or lock unfairness.

---

## 7️⃣ `volatile` — Misconceptions

### Q19. What problem does `volatile` solve?
**Answer:**
Visibility.
It ensures changes made by one thread are visible to others.

---

### Q20. Is `volatile` thread-safe?
**Answer:**
No.
It does not provide atomicity.

---

### Q21. When is `volatile` useful?
**Answer:**
For flags and state signals (start/stop, ready flags).

---

## 8️⃣ Atomic Variables & CAS

### Q22. Why were atomic classes introduced?
**Answer:**
To provide lock-free, thread-safe operations using CAS.

---

### Q23. When are atomics NOT enough?
**Answer:**
When multiple variables or complex invariants must be updated atomically.

---

### Q24. What is the ABA problem?
**Answer:**
A value changes from A → B → A,
making CAS think nothing changed.

---

## 9️⃣ ExecutorService & Thread Pools

### Q25. Why not create threads manually?
**Answer:**
Thread creation is expensive.
Thread pools reuse threads and manage lifecycle efficiently.

---

### Q26. Difference between `execute()` and `submit()`?
**Answer:**
- `execute()` → Runnable, no result
- `submit()` → Runnable/Callable, returns Future

---

### Q27. What happens if you forget to call `shutdown()`?
**Answer:**
JVM may not exit because threads are still alive.

---

## 1️⃣0️⃣ BlockingQueue & Producer–Consumer

### Q28. Why prefer `BlockingQueue` over `wait/notify`?
**Answer:**
It is simpler, safer, and less error-prone.
Blocking behavior is built into the API.

---

### Q29. Difference between `put()` and `offer()`?
**Answer:**
- `put()` blocks if queue is full
- `offer()` returns immediately (or after timeout)

---

## 1️⃣1️⃣ ThreadLocal (Very Dangerous)

### Q30. Why is ThreadLocal dangerous with thread pools?
**Answer:**
Threads are reused.
Old values can leak into new tasks.

---

### Q31. What is the golden rule of ThreadLocal?
**Answer:**
Always call `remove()` after use.

---

## 1️⃣2️⃣ Async & CompletableFuture Traps

### Q32. Why should we avoid `get()` or `join()` on request threads?
**Answer:**
They block threads and reduce throughput.

---

### Q33. Where do exceptions go in CompletableFuture?
**Answer:**
They are captured in the future and must be handled explicitly.

---

## 🔑 One-Line Interview Shields

Use these to stop pressure:

- “This is a visibility issue, not atomicity.”
- “That lock is held on the object, not the method.”
- “This is a scheduling-dependent race condition.”
- “That exception won’t propagate across threads.”

---

## ✅ Status

✔ Thread lifecycle traps  
✔ Object vs Thread confusion  
✔ Locking & visibility  
✔ Deadlock & livelock  
✔ Atomic vs synchronized  
✔ Thread pools & async  
✔ Backend concurrency behavior  

This file is designed to make you **multithreading-safe under indirect questioning**.

---
