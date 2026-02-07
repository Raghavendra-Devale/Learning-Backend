# Multithreading – Lesson 8  
## Atomic Variables & Compare-And-Swap (CAS)

These notes explain why atomic variables exist in Java, how they work internally using CAS, and when they should or should not be used.

---

## 1. Why Atomic Variables Were Introduced

Atomic variables were introduced to:
- Provide thread-safe operations without using locks
- Avoid performance overhead of synchronized
- Support scalable, non-blocking concurrency

They solve problems where `volatile` is insufficient and `synchronized` is too heavy.

---

## 2. What Are Atomic Classes?

Common atomic classes:
- AtomicInteger
- AtomicLong
- AtomicBoolean
- AtomicReference

They provide:
- Atomic operations
- Visibility guarantee
- Lock-free behavior

---

## 3. Compare-And-Swap (CAS)

CAS is a low-level atomic operation supported by hardware.

How CAS works:
1. Read the current value
2. Compare with an expected value
3. If equal, update to a new value
4. If not, retry

This entire operation is atomic.

---

## 4. Why CAS Is Important

CAS enables:
- Lock-free updates
- High concurrency
- No blocking
- Better scalability under contention

Multiple threads may retry, but only one succeeds per update.

---

## 5. Atomic Operations Example

Instead of:
```java
count++;
````

Use:

```java
AtomicInteger count = new AtomicInteger(0);
count.incrementAndGet();
```

This increment is atomic and thread-safe.

---

## 6. Atomic vs volatile vs synchronized

* volatile → visibility only
* Atomic → atomicity + visibility (single variable)
* synchronized → atomicity + visibility (multiple operations)

Each has a different purpose.

---

## 7. Limitations of Atomic Variables

Atomic variables:

* Work best for single-variable updates
* Do not coordinate multiple variables
* Cannot maintain complex invariants

For multi-step logic, synchronization or locks are required.

---

## 8. ABA Problem

CAS can suffer from the ABA problem:

* Value changes A → B → A
* CAS assumes nothing changed
* Leads to incorrect behavior

Java provides:

* AtomicStampedReference
* AtomicMarkableReference

These help detect intermediate changes.

---

## 9. Backend Use Cases

Atomic variables are commonly used in:

* Counters
* Metrics
* Rate limiters
* Statistics
* Simple shared state

---

## 10. Interview-Safe Summary

> “Atomic variables provide lock-free, thread-safe operations using CAS, ensuring atomicity and visibility for single variables without synchronized.”

---

