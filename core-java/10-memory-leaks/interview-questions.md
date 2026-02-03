
# Interview Questions – Java Memory Leaks & Weak References

---

## Q1. Can Java have memory leaks even with GC?
**Answer:**
Yes. Memory leaks occur when objects remain reachable from GC Roots and cannot be reclaimed.

---

## Q2. What are GC Roots?
**Answer:**
GC Roots include static variables, active threads, stack frames, and JNI references.

---

## Q3. Why are static variables dangerous?
**Answer:**
Because they live for the entire JVM lifetime and keep referenced objects reachable.

---

## Q4. Why are collections a common cause of leaks?
**Answer:**
Because collections retain references unless elements are explicitly removed.

---

## Q5. Why is ThreadLocal a common source of memory leaks?
**Answer:**
ThreadLocal values remain attached to long-lived threads in thread pools unless removed explicitly.

---

## Q6. What is WeakHashMap and when should it be used?
**Answer:**
WeakHashMap stores keys using weak references and should be used for caches or metadata where entries should be removed automatically when keys are no longer referenced.

---

## Common Interview Traps & Pitfalls

❌ Assuming GC prevents all memory leaks  
❌ Forgetting ThreadLocal.remove()  
❌ Using static caches without eviction  
❌ Thinking leaks are caused by missing free()  

---

## One Interview-Safe Explanation

> “Java memory leaks occur when objects remain reachable from GC Roots. Static references, collections, listeners, and ThreadLocal misuse are common causes. Weak references help prevent leaks.”
