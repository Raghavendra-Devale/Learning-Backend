## Multithreading – Lesson 7 (Complete Coverage)


# Interview Questions – Multithreading (Lesson 7)

---

## Q1. What problem does volatile solve?
**Answer:**
It solves visibility problems where threads may see stale values.

---

## Q2. What guarantee does volatile provide?
**Answer:**
Visibility guarantee—updates are immediately visible to all threads.

---

## Q3. Does volatile guarantee atomicity?
**Answer:**
No. volatile does not make compound operations atomic.

---

## Q4. Why is `count++` not thread-safe with volatile?
**Answer:**
Because increment involves read, modify, and write steps which are not atomic.

---

## Q5. Difference between volatile and synchronized?
**Answer:**
volatile provides visibility only, while synchronized provides mutual exclusion and visibility.

---

## Q6. Give a correct use case for volatile.
**Answer:**
A stop flag where one thread updates a boolean and other threads read it.

---

## Q7. Can volatile replace synchronized?
**Answer:**
No. volatile cannot replace synchronized when atomicity is required.

---

## Common Interview Traps & Pitfalls

❌ Saying volatile makes code thread-safe  
❌ Using volatile with ++ or --  
❌ Confusing visibility with atomicity  
❌ Overusing volatile for performance  
❌ Assuming volatile provides locking  

---

## One Interview-Safe Explanation

> “volatile ensures visibility across threads but does not provide atomicity or mutual exclusion.”

---