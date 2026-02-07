# Interview Questions – Multithreading (Lesson 3)

---

## Q1. What are the different thread states in Java?
**Answer:**
NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING, TERMINATED.

---

## Q2. What does RUNNABLE state mean?
**Answer:**
It means the thread is ready to run or currently running. Actual execution depends on OS scheduling.

---

## Q3. Why does RUNNABLE not mean running?
**Answer:**
Because thread scheduling is controlled by the operating system and is non-deterministic.

---

## Q4. When does a thread enter BLOCKED state?
**Answer:**
When it tries to acquire a lock held by another thread in a synchronized block or method.

---

## Q5. When does a thread enter WAITING state?
**Answer:**
When it waits indefinitely for another thread using methods like `wait()` or `join()`.

---

## Q6. Difference between WAITING and TIMED_WAITING?
**Answer:**
WAITING has no timeout, while TIMED_WAITING automatically wakes after a specified time.

---

## Q7. Which state does Thread.sleep() cause?
**Answer:**
TIMED_WAITING.

---

## Q8. Can a thread in WAITING state consume CPU?
**Answer:**
No. WAITING threads do not consume CPU.

---

## Q9. Can a TERMINATED thread be restarted?
**Answer:**
No. A thread is single-use and cannot be restarted once terminated.

---

## Q10. Why is BLOCKED always related to synchronized?
**Answer:**
Because BLOCKED occurs only when waiting to acquire a monitor lock.

---

## Common Interview Traps & Pitfalls

❌ Saying RUNNABLE means running  
❌ Confusing BLOCKED with WAITING  
❌ Saying sleep() causes BLOCKED  
❌ Thinking threads can be restarted  
❌ Ignoring OS scheduling  

---

## One Interview-Safe Explanation

> “RUNNABLE represents readiness, not guaranteed execution. BLOCKED is lock-related, WAITING is coordination-related, and TERMINATED threads cannot be restarted.”

---
