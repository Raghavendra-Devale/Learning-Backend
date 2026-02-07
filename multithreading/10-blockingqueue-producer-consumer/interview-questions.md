# Interview Questions – Multithreading (Lesson 10)

---

## Q1. What problem does BlockingQueue solve?
**Answer:**
It enables safe data exchange between threads without manual synchronization and avoids busy waiting.

---

## Q2. What does blocking mean in BlockingQueue?
**Answer:**
The thread waits automatically when the queue is full or empty and resumes when the condition changes.

---

## Q3. How does BlockingQueue help in producer–consumer pattern?
**Answer:**
Producers block when the queue is full and consumers block when it is empty, ensuring smooth coordination.

---

## Q4. Difference between put() and offer()?
**Answer:**
put() blocks indefinitely when the queue is full, while offer() returns immediately or after a timeout.

---

## Q5. Difference between take() and poll()?
**Answer:**
take() blocks when the queue is empty, while poll() returns immediately or after a timeout.

---

## Q6. Why is BlockingQueue preferred over wait/notify?
**Answer:**
It is simpler, safer, less error-prone, and handles synchronization internally.

---

## Q7. Why are bounded queues preferred in backend systems?
**Answer:**
They provide backpressure and prevent uncontrolled memory growth.

---

## Common Interview Traps & Pitfalls

❌ Busy-waiting instead of blocking  
❌ Using unbounded queues blindly  
❌ Mixing wait/notify with BlockingQueue  
❌ Ignoring backpressure  
❌ Misunderstanding blocking vs sleeping  

---

## One Interview-Safe Explanation

> “BlockingQueue simplifies producer–consumer coordination by providing built-in blocking and thread safety.”

---
