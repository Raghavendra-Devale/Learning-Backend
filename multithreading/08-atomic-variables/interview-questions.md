
# Interview Questions – Multithreading (Lesson 8)

---

## Q1. Why were atomic classes introduced?
**Answer:**
To provide thread-safe, lock-free operations with better performance and scalability than synchronized.

---

## Q2. What is Compare-And-Swap (CAS)?
**Answer:**
CAS is an atomic operation that updates a value only if it matches an expected value, enabling non-blocking concurrency.

---

## Q3. How do atomic classes achieve thread safety?
**Answer:**
By using CAS at the hardware level along with visibility guarantees.

---

## Q4. Difference between atomic and synchronized?
**Answer:**
Atomic classes use lock-free CAS for single variables, while synchronized uses locks and supports multi-step logic.

---

## Q5. When are atomic variables NOT enough?
**Answer:**
When multiple variables must be updated together or complex invariants must be maintained.

---

## Q6. What is the ABA problem?
**Answer:**
A scenario where a value changes from A to B and back to A, causing CAS to incorrectly assume no change occurred.

---

## Q7. How does Java address the ABA problem?
**Answer:**
Using AtomicStampedReference or AtomicMarkableReference.

---

## Common Interview Traps & Pitfalls

❌ Thinking atomic variables replace synchronized  
❌ Using atomic variables for multi-variable logic  
❌ Ignoring ABA problem  
❌ Assuming atomic operations never retry  
❌ Overusing atomics instead of higher-level constructs  

---

## One Interview-Safe Explanation

> “Atomic classes provide lock-free, thread-safe operations using CAS. They are ideal for single-variable updates but not for complex coordination.”

---