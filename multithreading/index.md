# 🧵 Java Multithreading — Complete Notes & Interview Prep

This section contains **end-to-end, interview-focused multithreading notes**, built from fundamentals to advanced async programming.

The content is structured lesson-wise so each topic can be revised independently before interviews.

---

## 🧵 Multithreading Index

### 00. Why Multithreading Exists

**Concepts**
- CPU idle time & I/O wait
- Concurrency vs parallelism
- Why threads were introduced

- 📘 [Notes](./00-why-multithreading/notes.md)
- 🎯 [Interview Questions](./00-why-multithreading/interview-questions.md)

---

### 01. Process vs Thread & Memory Model

**Concepts**
- Process vs thread
- Stack vs heap
- Why stack is thread-local
- Shared heap problems

- 📘 [Notes](./01-process-vs-thread/notes.md)
- 🎯 [Interview Questions](./01-process-vs-thread/interview-questions.md)

---

### 02. Creating Threads

**Concepts**
- `Thread` vs `Runnable`
- `start()` vs `run()`
- Why extending Thread is bad design
- Thread lifecycle basics

- 📘 [Notes](./02-creating-threads/notes.md)
- 🎯 [Interview Questions](./02-creating-threads/interview-questions.md)

---

### 03. Thread Lifecycle & States

**Concepts**
- NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING, TERMINATED
- BLOCKED vs WAITING (very important)
- Why threads look “stuck”

- 📘 [Notes](./03-thread-lifecycle/notes.md)
- 🎯 [Interview Questions](./03-thread-lifecycle/interview-questions.md)

---

### 04. Race Conditions & Data Inconsistency

**Concepts**
- Shared mutable state
- Why `count++` is not atomic
- Timing-dependent bugs (Heisenbugs)
- Read vs write safety

- 📘 [Notes](./04-race-conditions/notes.md)
- 🎯 [Interview Questions](./04-race-conditions/interview-questions.md)

---

### 05. Synchronization (`synchronized`)

**Concepts**
- Monitor lock
- Object-level vs class-level locking
- Method vs block synchronization
- Visibility guarantee

- 📘 [Notes](./05-synchronization/notes.md)
- 🎯 [Interview Questions](./05-synchronization/interview-questions.md)

---

### 06. Deadlock, Livelock & Starvation

**Concepts**
- Deadlock conditions
- Circular wait
- Livelock vs deadlock
- Starvation & fairness

- 📘 [Notes](./06-deadlock-livelock-starvation/notes.md)
- 🎯 [Interview Questions](./06-deadlock-livelock-starvation/interview-questions.md)

---

### 07. `volatile`

**Concepts**
- Visibility vs atomicity
- Instruction reordering
- Why `volatile` ≠ thread-safe
- Correct & incorrect use cases

- 📘 [Notes](./07-volatile/notes.md)
- 🎯 [Interview Questions](./07-volatile/interview-questions.md)

---

### 08. Atomic Variables & CAS

**Concepts**
- `AtomicInteger`, `AtomicLong`
- Compare-And-Swap (CAS)
- Atomic vs synchronized
- ABA problem (awareness level)

- 📘 [Notes](./08-atomic-variables/notes.md)
- 🎯 [Interview Questions](./08-atomic-variables/interview-questions.md)

---

### 09. ExecutorService & Thread Pools

**Concepts**
- Why not `new Thread()`
- Task vs thread
- `execute()` vs `submit()`
- `Callable` & `Future`
- Importance of `shutdown()`

- 📘 [Notes](./09-executorservice-threadpools/notes.md)
- 🎯 [Interview Questions](./09-executorservice-threadpools/interview-questions.md)

---

### 10. BlockingQueue & Producer–Consumer

**Concepts**
- Blocking vs busy waiting
- `put()` vs `offer()`
- Backpressure
- Why BlockingQueue > wait/notify

- 📘 [Notes](./10-blockingqueue-producer-consumer/notes.md)
- 🎯 [Interview Questions](./10-blockingqueue-producer-consumer/interview-questions.md)

---

### 11. ThreadLocal

**Concepts**
- Per-thread isolation
- Real backend use cases
- ThreadLocal + thread pool memory leaks
- Mandatory `remove()`

- 📘 [Notes](./11-threadlocal/notes.md)
- 🎯 [Interview Questions](./11-threadlocal/interview-questions.md)

---

### 12. CompletableFuture & Async Programming

**Concepts**
- Blocking vs non-blocking
- `thenApply` vs `thenCompose`
- `allOf()` / `anyOf()`
- Exception handling
- Why not to block request threads

- 📘 [Notes](./12-completablefuture/notes.md)
- 🎯 [Interview Questions](./12-completablefuture/interview-questions.md)

---

## 🎯 How to Use This for Interviews
- **Freshers** → Revise Lessons 1–7 thoroughly
- **1–3 YOE** → Revise all lessons + traps
- **Before interview** → Read only `interview-questions.md`

---

## 🧠 Author’s Note

These notes were created while preparing for **Java Backend interviews**, with focus on:
- Conceptual clarity
- Internal working
- Real backend relevance
- Common interviewer traps
