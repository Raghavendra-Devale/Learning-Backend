# Multithreading – Lesson 11  
## ThreadLocal (Per-Thread State Without Synchronization)

These notes explain why ThreadLocal exists, how it works conceptually, its real backend use cases, and the critical pitfalls associated with thread pools.

---

## 1. What Problem ThreadLocal Solves

ThreadLocal provides each thread with its own isolated copy of a variable.

It is used when:
- Data should not be shared across threads
- Passing data through multiple method calls is impractical
- Synchronization is undesirable or unnecessary

ThreadLocal avoids shared-state concurrency issues by design.

---

## 2. What ThreadLocal Really Does

ThreadLocal does not store data globally.

Conceptually:
- Each thread maintains its own internal map
- Key → ThreadLocal instance
- Value → data specific to that thread

Same ThreadLocal variable, different value per thread.

---

## 3. Why ThreadLocal Does Not Need Synchronization

ThreadLocal does not require synchronization because:
- Each thread accesses only its own data
- No other thread can read or modify that value
- There is no shared mutable state

Isolation replaces synchronization.

---

## 4. Common Backend Use Cases

ThreadLocal is commonly used for:
- Request context (userId, requestId, traceId)
- Transaction context
- Security context
- Logging frameworks (MDC)

These are per-request, per-thread concerns.

---

## 5. ThreadLocal and Thread Pools (CRITICAL)

Thread pools reuse threads.

This means:
- ThreadLocal values remain attached to the thread
- Threads do not die after a request
- Old data can leak into subsequent tasks

This can cause:
- Memory leaks
- Data leakage between requests
- Security issues

---

## 6. Why Memory Leaks Occur

If ThreadLocal values are:
- Set
- But never removed

Then:
- Data remains referenced
- Garbage collection cannot clean it
- Memory usage grows over time

This is a common production issue.

---

## 7. The Golden Rule

Always clean up ThreadLocal values.

Best practice:
- Call `remove()` in a `finally` block
- Ensure cleanup after request or task completion

Never assume thread lifecycle equals request lifecycle.

---

## 8. When to Use ThreadLocal (And When Not To)

Use ThreadLocal only when:
- Data is strictly per-thread
- Lifecycle is well-defined
- Cleanup is guaranteed

Avoid using ThreadLocal for:
- Business data
- Large objects
- Long-lived threads without cleanup

---

## 9. Backend Reality

ThreadLocal is powerful but dangerous.

Senior engineers:
- Use it sparingly
- Understand thread pool implications
- Always ensure cleanup

---

## 10. Interview-Safe Summary

> “ThreadLocal provides per-thread isolated variables without synchronization, but improper cleanup in thread pools can cause memory leaks and data leakage.”

---
