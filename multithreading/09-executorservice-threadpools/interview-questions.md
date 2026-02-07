## Multithreading – Lesson 9 (Complete Coverage)

# Interview Questions – Multithreading (Lesson 9)

---

## Q1. Why is creating threads manually discouraged?
**Answer:**
Threads are heavyweight and expensive to create. Excessive thread creation causes memory and CPU overhead.

---

## Q2. What problem do thread pools solve?
**Answer:**
They reuse a fixed number of threads to execute many tasks, improving performance and stability.

---

## Q3. Difference between task and thread?
**Answer:**
A task represents what to execute, while a thread represents how it is executed.

---

## Q4. Difference between execute() and submit()?
**Answer:**
execute() returns nothing, while submit() returns a Future and captures exceptions.

---

## Q5. Why is submit() often preferred?
**Answer:**
Because it allows tracking task completion and handling exceptions.

---

## Q6. What is Callable?
**Answer:**
A task that returns a value and can throw checked exceptions.

---

## Q7. Why is shutdown important?
**Answer:**
To release thread resources and prevent memory leaks.

---

## Q8. What happens if ExecutorService is not shut down?
**Answer:**
Threads remain alive, causing resource leaks and preventing application termination.

---

## Common Interview Traps & Pitfalls

❌ Creating threads per request  
❌ Forgetting to shutdown ExecutorService  
❌ Confusing tasks with threads  
❌ Using cached thread pool blindly  
❌ Ignoring exception handling in execute()  

---

## One Interview-Safe Explanation

> “Thread pools reuse a limited number of threads to execute tasks efficiently, preventing resource exhaustion.”

---