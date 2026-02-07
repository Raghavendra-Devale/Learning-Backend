# Multithreading – Lesson 9  
## ExecutorService & Thread Pools

These notes explain why thread pools are used in Java, how ExecutorService works, and why manual thread creation is discouraged in backend systems.

---

## 1. Why Manual Thread Creation Is a Problem

Threads are heavyweight because:
- Each thread has its own stack
- OS-level resources are involved
- Excessive threads cause context switching overhead

Creating threads per task leads to poor performance and instability.

---

## 2. Core Idea of Thread Pools

Thread pools:
- Create a fixed number of threads
- Reuse them to execute many tasks
- Limit concurrency
- Improve resource utilization

Threads are expensive, tasks are cheap.

---

## 3. What Is ExecutorService?

ExecutorService is a high-level API for:
- Managing a pool of threads
- Submitting tasks for execution
- Handling lifecycle of threads

It separates task submission from thread management.

---

## 4. Task vs Thread

- Task → Runnable / Callable (what to execute)
- Thread → execution mechanism (how it runs)

ExecutorService executes tasks using pooled threads.

---

## 5. execute() vs submit()

### execute()
- Accepts Runnable
- Returns nothing
- Exceptions go to thread’s uncaught handler

### submit()
- Accepts Runnable or Callable
- Returns a Future
- Exceptions are captured in the Future

submit() is generally preferred.

---

## 6. Callable vs Runnable

- Runnable → no return value
- Callable → returns a value and can throw checked exceptions

Callable is used when results are needed.

---

## 7. Common Thread Pool Types (High-Level)

- Fixed thread pool → constant number of threads
- Cached thread pool → dynamic thread creation
- Single-thread executor → ordered execution

Fixed thread pools are safest for backend systems.

---

## 8. Importance of shutdown()

ExecutorService must be shut down:
- shutdown() → graceful shutdown
- shutdownNow() → forceful shutdown

Not shutting down leads to resource leaks.

---

## 9. Backend Reality

Thread pools are used everywhere:
- Web servers
- Database connection pools
- Async processing
- Spring’s @Async

Understanding thread pools is essential for scalable backend systems.

---

## 10. Interview-Safe Summary

> “ExecutorService manages a pool of reusable threads, allowing tasks to be executed efficiently without manual thread management.”

---


