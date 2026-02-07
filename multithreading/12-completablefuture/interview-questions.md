# Interview Questions – Multithreading (Lesson 12)

---

## Q1. Why was CompletableFuture introduced?
**Answer:**
To support non-blocking async programming with better composition and readability than Future.

---

## Q2. Difference between blocking and non-blocking?
**Answer:**
Blocking waits and holds the thread, while non-blocking allows the thread to continue and react later.

---

## Q3. Difference between thenApply and thenCompose?
**Answer:**
thenApply transforms a value, while thenCompose flattens nested CompletableFutures.

---

## Q4. When would you use allOf()?
**Answer:**
When multiple async tasks must complete before proceeding, such as aggregating parallel service calls.

---

## Q5. How does CompletableFuture handle exceptions?
**Answer:**
Exceptions must be handled explicitly using methods like exceptionally() or handle().

---

## Q6. Difference between join() and get()?
**Answer:**
Both block, but get() throws checked exceptions while join() throws unchecked exceptions.

---

## Q7. Why should join()/get() be avoided in request threads?
**Answer:**
They block request threads, reducing throughput and scalability.

---

## Common Interview Traps & Pitfalls

❌ Blocking inside async pipelines  
❌ Using thenApply when thenCompose is required  
❌ Ignoring exception handling  
❌ Assuming async always means faster  
❌ Using ForkJoinPool blindly  

---

## One Interview-Safe Explanation

> “CompletableFuture enables non-blocking, composable async pipelines, allowing backend systems to scale efficiently without blocking request threads.”

---