
# 🎯 Java Multithreading — COMPLETE Interview Question Bank

## 0️⃣ Warm-up / Screening Questions

(Used in first 5 minutes)

1. What is multithreading?
2. Why do we need multithreading?
3. Difference between concurrency and parallelism?
4. What is a process?
5. What is a thread?
6. Why are threads called lightweight?
7. Can a Java program run without threads?
8. How many threads run by default in a Java program?

---

## 1️⃣ Process vs Thread & Memory Model

1. Difference between process and thread?
2. Which memory is shared between threads?
3. Why does each thread have its own stack?
4. What is stored in stack memory?
5. What is stored in heap memory?
6. What happens to stack memory when a method finishes?
7. Why is heap shared across threads?
8. Why does stack overflow occur?
9. Can stack memory cause memory leaks?
10. Can heap memory cause memory leaks?
11. What happens if two threads modify heap data simultaneously?

**Trap follow-up:**

* If stacks are separate, why do race conditions still happen?

---

## 2️⃣ Creating Threads

1. How do you create a thread in Java?
2. Difference between extending `Thread` and implementing `Runnable`?
3. Why is implementing `Runnable` preferred?
4. What is tight coupling in Thread inheritance?
5. Difference between `start()` and `run()`?
6. What happens internally when `start()` is called?
7. Can we call `run()` directly?
8. What happens if we call `start()` twice?

**Trap question:**

* Does calling `run()` create a new thread?

---

## 3️⃣ Thread Lifecycle & States

1. What are the thread states in Java?
2. Difference between NEW and RUNNABLE?
3. Is RUNNABLE always running?
4. Difference between BLOCKED and WAITING?
5. When does a thread go into BLOCKED state?
6. When does a thread go into WAITING state?
7. What is TIMED_WAITING?
8. Can a thread go from TERMINATED to RUNNABLE?
9. Why can’t a thread be restarted?
10. How does OS scheduling affect threads?

---

## 4️⃣ Race Conditions & Data Inconsistency

1. What is a race condition?
2. When does a race condition occur?
3. Why is `count++` not thread-safe?
4. Is increment atomic?
5. What are timing-dependent bugs?
6. Why are race conditions hard to reproduce?
7. Can race conditions occur without shared memory?
8. Is reading shared data safe?
9. What happens if only one thread writes?
10. Give a real backend example of race condition.

**Trap:**

* Are primitive variables thread-safe?

---

## 5️⃣ Synchronization (`synchronized`)

1. What problem does `synchronized` solve?
2. What is mutual exclusion?
3. What is visibility guarantee?
4. Where is the lock stored?
5. Is lock on code or object?
6. Difference between synchronized method and block?
7. Which lock is used in instance synchronized method?
8. Which lock is used in static synchronized method?
9. What is object-level locking?
10. What is class-level locking?
11. Can two threads enter synchronized methods on different objects?
12. Can synchronized cause performance issues?
13. Does synchronized guarantee fairness?
14. Does synchronized prevent deadlock?

**Trap:**

* Is synchronized slow by default?

---

## 6️⃣ Deadlock, Livelock & Starvation

1. What is deadlock?
2. What causes deadlock?
3. What is circular wait?
4. What are the four deadlock conditions?
5. Can JVM detect deadlocks?
6. Does deadlock throw an exception?
7. What is livelock?
8. Difference between deadlock and livelock?
9. What is starvation?
10. How does starvation occur?
11. Does synchronized prevent deadlock?
12. How do you prevent deadlocks?

**Scenario:**

* Two services holding DB + file locks — explain deadlock.

---

## 7️⃣ `volatile`

1. What problem does volatile solve?
2. What is visibility problem?
3. Does volatile guarantee atomicity?
4. Does volatile guarantee mutual exclusion?
5. Why `volatile int count` is not thread-safe?
6. Difference between volatile and synchronized?
7. What is instruction reordering?
8. How volatile prevents reordering?
9. Correct use cases of volatile?
10. Wrong use cases of volatile?

**Trap:**

* Can volatile replace synchronized?

---

## 8️⃣ Atomic Variables & CAS

1. What are atomic classes?
2. Why were atomic variables introduced?
3. What is CAS?
4. How does CAS work internally?
5. Is CAS lock-free?
6. Atomic vs synchronized?
7. Atomic vs volatile?
8. When are atomic variables not enough?
9. What is ABA problem?
10. How does Java solve ABA problem?

**Trap:**

* Are atomic operations always faster?

---

## 9️⃣ ExecutorService & Thread Pools

1. Why not create threads manually?
2. What is a thread pool?
3. What problem do thread pools solve?
4. Difference between task and thread?
5. What is ExecutorService?
6. Difference between execute() and submit()?
7. What is Callable?
8. Callable vs Runnable?
9. What is Future?
10. How do you get result from Future?
11. What happens if you don’t shutdown executor?
12. Difference between shutdown() and shutdownNow()?
13. Which thread pool is safest for backend?

**Trap:**

* Is cached thread pool safe?

---

## 🔟 BlockingQueue & Producer–Consumer

1. What is BlockingQueue?
2. What does blocking mean?
3. Difference between blocking and busy waiting?
4. How does BlockingQueue help producer–consumer?
5. put() vs offer()?
6. take() vs poll()?
7. What happens when queue is full?
8. Why are bounded queues important?
9. BlockingQueue vs wait/notify?
10. Where is BlockingQueue used internally?

---

## 1️⃣1️⃣ ThreadLocal

1. What is ThreadLocal?
2. What problem does ThreadLocal solve?
3. How does ThreadLocal work conceptually?
4. Why ThreadLocal doesn’t need synchronization?
5. Give real backend use case.
6. Why ThreadLocal is dangerous with thread pools?
7. What causes ThreadLocal memory leaks?
8. How do you prevent ThreadLocal memory leaks?
9. When should ThreadLocal NOT be used?
10. What is the golden rule of ThreadLocal?

**Trap:**

* Is ThreadLocal data garbage collected automatically?

---

## 1️⃣2️⃣ CompletableFuture & Async

1. Why was CompletableFuture introduced?
2. Future vs CompletableFuture?
3. Blocking vs non-blocking?
4. supplyAsync vs runAsync?
5. thenApply vs thenCompose?
6. allOf() vs anyOf()?
7. How do you handle exceptions?
8. join() vs get()?
9. Why should join/get be avoided in request threads?
10. Async vs multithreading?
11. What executor does CompletableFuture use by default?
12. When should you provide custom executor?

**Trap:**

* Does async always mean faster?

---

## 🔥 FINAL RAPID-FIRE QUESTIONS (HR + Senior Round)

1. What is the biggest mistake juniors make in multithreading?
2. Which is worse: deadlock or race condition?
3. When would you choose synchronized over atomic?
4. When would you choose atomic over synchronized?
5. What multithreading bug have you debugged?
6. How does Spring handle threading?
7. What happens under high load?
8. How do you design thread-safe code?
9. What would you never do in production?
10. Explain multithreading in one minute.

---

## 🧠 ONE-LINE MASTER ANSWER (Memorize)

> “Multithreading improves throughput by allowing concurrent execution, but shared mutable state must be carefully controlled using synchronization, atomic operations, or isolation to avoid race conditions, deadlocks, and memory leaks.”

---