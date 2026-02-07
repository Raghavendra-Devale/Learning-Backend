# Interview Questions – Multithreading (Lesson 2)

---

## Q1. Difference between run() and start()?
**Answer:**
run() executes like a normal method on the current thread, while start() creates a new thread and invokes run() internally.

---

## Q2. Does calling run() create a new thread?
**Answer:**
No. Calling run() does not create a new thread.

---

## Q3. What happens if start() is called twice on the same thread?
**Answer:**
It throws IllegalThreadStateException because a thread cannot be restarted once terminated.

---

## Q4. Why is extending Thread discouraged?
**Answer:**
Because it causes tight coupling between task and execution, prevents inheritance from other classes, and reduces reusability.

---

## Q5. Why is Runnable preferred?
**Answer:**
Runnable separates task logic from execution, provides loose coupling, and works well with thread pools.

---

## Q6. Can a thread be reused?
**Answer:**
No. Threads are single-use; tasks are reusable.

---

## Q7. Which method should be overridden: run() or start()?
**Answer:**
run() should be overridden. start() should never be overridden.

---

## Common Interview Traps & Pitfalls

❌ Saying run() creates a thread  
❌ Overriding start()  
❌ Restarting a thread  
❌ Saying Thread and Runnable are the same  
❌ Using Thread directly in production code  

---

## One Interview-Safe Explanation

> “start() creates a new thread and calls run() internally. run() is just the task logic. Runnable is preferred over extending Thread because it promotes loose coupling and reusability.”

---