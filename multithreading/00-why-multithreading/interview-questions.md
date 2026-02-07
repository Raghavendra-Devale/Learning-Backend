# Interview Questions – Multithreading (Level 0)

---

## Q1. Why was multithreading introduced?
**Answer:**
To prevent CPU idle time by allowing a program to perform useful work while waiting for I/O operations.

---

## Q2. What problem does multithreading solve?
**Answer:**
It improves CPU utilization, throughput, and responsiveness by enabling concurrent execution paths.

---

## Q3. What is the difference between multitasking and multithreading?
**Answer:**
Multitasking runs multiple processes at the OS level, while multithreading runs multiple threads within the same process sharing memory.

---

## Q4. Why are threads preferred over processes?
**Answer:**
Threads are lightweight, faster to create, and can communicate efficiently by sharing memory.

---

## Q5. Who schedules Java threads?
**Answer:**
The operating system schedules Java threads; scheduling is non-deterministic.

---

## Q6. Is multithreading mainly about speed?
**Answer:**
No. It is mainly about better resource utilization and responsiveness; speedup depends on workload and CPU cores.

---

## Common Interview Traps & Pitfalls

❌ Saying multithreading always improves performance  
❌ Confusing multitasking with multithreading  
❌ Assuming Java controls thread scheduling  
❌ Ignoring I/O wait as the motivation for threads  
❌ Equating concurrency with parallelism  

---

## One Interview-Safe Explanation

> “Multithreading allows a program to keep the CPU busy by performing other tasks while waiting for I/O, improving responsiveness and throughput.”

---
