# Interview Questions – Multithreading (Lesson 6)

---

## Q1. What is a deadlock?
**Answer:**
A deadlock occurs when two or more threads are permanently blocked, each waiting for resources held by the others.

---

## Q2. Why does circular wait cause deadlock?
**Answer:**
Because each thread holds a resource and waits for another in a cycle, so none can proceed.

---

## Q3. What are the conditions required for deadlock?
**Answer:**
Mutual exclusion, hold and wait, no preemption, and circular wait.

---

## Q4. Difference between deadlock and livelock?
**Answer:**
Deadlock involves blocked threads, while livelock involves active threads making no progress.

---

## Q5. What is starvation?
**Answer:**
Starvation occurs when a thread never gets CPU time or lock access due to unfair scheduling.

---

## Q6. Does synchronized prevent deadlocks?
**Answer:**
No. synchronized ensures mutual exclusion but does not prevent circular lock dependencies.

---

## Q7. Can deadlocks be fixed at runtime?
**Answer:**
No. They must be prevented through proper design.

---

## Common Interview Traps & Pitfalls

❌ Thinking synchronized avoids deadlock  
❌ Confusing livelock with deadlock  
❌ Ignoring fairness in starvation  
❌ Believing deadlocks always throw exceptions  
❌ Assuming JVM detects all deadlocks  

---

## One Interview-Safe Explanation

> “Deadlocks are caused by circular lock dependencies, livelocks involve active threads making no progress, and starvation results from unfair scheduling.”

---
