# Multithreading – Lesson 4  
## Race Conditions & Data Inconsistency

These notes explain what race conditions are, why they occur, and how shared mutable state leads to data inconsistency in multithreaded Java applications.

---

## 1. What Is a Race Condition?

A race condition occurs when:
- Multiple threads access shared data
- At least one thread modifies the data
- The final result depends on timing or execution order

The outcome becomes unpredictable.

---

## 2. Shared Mutable State

Race conditions require:
- Shared memory (heap)
- Mutable data
- Concurrent access

If shared data is immutable or read-only, race conditions do not occur.

---

## 3. Why `count++` Is Not Thread-Safe

The operation:
```java
count++;
````

Is not atomic. It expands to:

1. Read value from memory
2. Increment the value
3. Write value back to memory

When multiple threads interleave these steps, updates can be lost.

---

## 4. Example of Lost Update

Two threads incrementing `count`:

* Thread A reads 0
* Thread B reads 0
* Thread A writes 1
* Thread B writes 1

Expected result: 2
Actual result: 1

This is a race condition.

---

## 5. Data Inconsistency

Race conditions lead to:

* Lost updates
* Incorrect calculations
* Corrupted state
* Non-deterministic behavior

Such bugs may appear or disappear depending on timing.

---

## 6. Timing-Dependent Bugs

Race conditions are:

* Dependent on OS scheduling
* Dependent on JVM execution order
* Non-deterministic

They cannot be reliably reproduced.

These bugs are often called **Heisenbugs**.

---

## 7. Read vs Write Access

* Multiple threads reading shared data → safe
* At least one thread writing shared data → unsafe

This distinction is fundamental to concurrency control.

---

## 8. Why Java Allows This

Java does not synchronize by default because:

* Synchronization has performance cost
* Developers must explicitly define critical sections

This gives flexibility but requires discipline.

---

## 9. Backend Relevance

Race conditions commonly occur in:

* Counters
* In-memory caches
* Statistics
* ID generators
* Rate limiters

Any shared mutable state is a potential risk.

---

## 10. Interview-Safe Summary

> “A race condition occurs when multiple threads access shared mutable data concurrently and at least one modifies it, causing results to depend on timing.”

---




