# Interview Questions – Multithreading (Lesson 5)

---

## Q1. What problem does synchronized solve?
**Answer:**
It prevents race conditions by ensuring mutual exclusion and visibility of shared data.

---

## Q2. Where is the lock associated in synchronized?
**Answer:**
The lock is associated with an object, not the code.

---

## Q3. Difference between synchronized method and synchronized block?
**Answer:**
A synchronized method locks the entire method, while a synchronized block locks only the critical section, giving better control and performance.

---

## Q4. What is object-level locking?
**Answer:**
Locking based on a specific object instance. Threads must synchronize on the same object to achieve mutual exclusion.

---

## Q5. What is class-level locking?
**Answer:**
Locking on the Class object using static synchronized methods or synchronized(ClassName.class).

---

## Q6. What guarantees does synchronized provide?
**Answer:**
Mutual exclusion and visibility.

---

## Q7. Does synchronized guarantee fairness?
**Answer:**
No. There is no guarantee about which thread acquires the lock next.

---

## Q8. Can synchronized prevent deadlocks?
**Answer:**
No. Incorrect locking can still lead to deadlocks.

---

## Common Interview Traps & Pitfalls

❌ Thinking synchronized locks code  
❌ Assuming synchronized is always slow  
❌ Using different objects for synchronization  
❌ Forgetting visibility guarantee  
❌ Believing synchronized solves all concurrency issues  

---

## One Interview-Safe Explanation

> “synchronized ensures that only one thread executes a critical section at a time and guarantees visibility by using an object’s monitor lock.”

---
