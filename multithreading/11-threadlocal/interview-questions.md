# Interview Questions – Multithreading (Lesson 11)

---

## Q1. What problem does ThreadLocal solve?
**Answer:**
It provides each thread with its own isolated copy of a variable, avoiding shared-state conflicts.

---

## Q2. Why doesn’t ThreadLocal need synchronization?
**Answer:**
Because each thread accesses only its own value; no other thread can modify it.

---

## Q3. Give a real backend use case for ThreadLocal.
**Answer:**
Storing request context such as userId or traceId for logging or transaction tracing.

---

## Q4. Why is ThreadLocal dangerous with thread pools?
**Answer:**
Because threads are reused, so ThreadLocal values can leak into subsequent tasks if not removed.

---

## Q5. What causes memory leaks with ThreadLocal?
**Answer:**
Failing to remove ThreadLocal values, causing them to remain referenced by long-lived threads.

---

## Q6. What is the golden rule when using ThreadLocal?
**Answer:**
Always call remove() after use, typically in a finally block.

---

## Q7. Is ThreadLocal thread-safe?
**Answer:**
It avoids sharing by design, so synchronization is not required.

---

## Common Interview Traps & Pitfalls

❌ Assuming ThreadLocal data is automatically cleaned  
❌ Forgetting to call remove()  
❌ Using ThreadLocal for business data  
❌ Ignoring thread pool reuse  
❌ Confusing ThreadLocal with shared variables  

---

## One Interview-Safe Explanation

> “ThreadLocal provides per-thread isolated state without synchronization, but must be cleaned up carefully in thread pools to avoid memory leaks.”

---