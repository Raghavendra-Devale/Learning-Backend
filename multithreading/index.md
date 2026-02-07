# 🧵 Java Multithreading — Complete Notes & Interview Prep

This repository contains **end-to-end, interview-focused Java multithreading notes**, covering everything from fundamentals to advanced asynchronous programming.

The content is organized **lesson-wise**, allowing each topic to be revised independently before interviews.

---

## 🧵 Multithreading Index

### 00. Why Multithreading Exists

**Key Concepts**
- CPU idle time & I/O wait
- Concurrency vs parallelism
- Why threads were introduced

📂 **00-why-multithreading/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 01. Process vs Thread & Memory Model

**Key Concepts**
- Process vs thread
- Stack vs heap memory
- Why stack memory is thread-local
- Problems with shared heap

📂 **01-process-vs-thread/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 02. Creating Threads

**Key Concepts**
- `Thread` vs `Runnable`
- `start()` vs `run()`
- Why extending `Thread` is poor design
- Thread lifecycle basics

📂 **02-creating-threads/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 03. Thread Lifecycle & States

**Key Concepts**
- NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING, TERMINATED
- BLOCKED vs WAITING (important interview topic)
- Common reasons threads appear “stuck”

📂 **03-thread-lifecycle/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 04. Race Conditions & Data Inconsistency

**Key Concepts**
- Shared mutable state
- Why `count++` is not atomic
- Timing-dependent bugs (Heisenbugs)
- Read vs write safety

📂 **04-race-conditions/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 05. Synchronization (`synchronized`)

**Key Concepts**
- Monitor lock
- Object-level vs class-level locking
- Method vs block synchronization
- Visibility guarantees

📂 **05-synchronization/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 06. Deadlock, Livelock & Starvation

**Key Concepts**
- Deadlock conditions
- Circular wait
- Livelock vs deadlock
- Starvation and fairness

📂 **06-deadlock-livelock-starvation/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 07. `volatile`

**Key Concepts**
- Visibility vs atomicity
- Instruction reordering
- Why `volatile` ≠ thread-safe
- Correct and incorrect use cases

📂 **07-volatile/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 08. Atomic Variables & CAS

**Key Concepts**
- `AtomicInteger`, `AtomicLong`
- Compare-And-Swap (CAS)
- Atomic variables vs `synchronized`
- ABA problem (awareness level)

📂 **08-atomic-variables/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 09. ExecutorService & Thread Pools

**Key Concepts**
- Why not `new Thread()`
- Task vs thread
- `execute()` vs `submit()`
- `Callable` and `Future`
- Importance of `shutdown()`

📂 **09-executorservice-threadpools/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 10. BlockingQueue & Producer–Consumer

**Key Concepts**
- Blocking vs busy waiting
- `put()` vs `offer()`
- Backpressure
- Why `BlockingQueue` > `wait/notify`

📂 **10-blockingqueue-producer-consumer/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 11. ThreadLocal

**Key Concepts**
- Per-thread data isolation
- Real backend use cases
- ThreadLocal + thread pool memory leaks
- Mandatory `remove()`

📂 **11-threadlocal/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

### 12. CompletableFuture & Async Programming

**Key Concepts**
- Blocking vs non-blocking
- `thenApply` vs `thenCompose`
- `allOf()` and `anyOf()`
- Exception handling
- Why request threads should not be blocked

📂 **12-completablefuture/**
- 📘 `notes.md`
- 🎯 `interview-questions.md`

---

## 🎯 How to Use This for Interviews

- **Freshers** → Revise Lessons 01–07 thoroughly
- **1–3 YOE** → Revise all lessons and common traps
- **Before interview** → Read only `interview-questions.md`

---

## 🧠 Author’s Note

These notes were created while preparing for **Java Backend interviews**, with a focus on:
- Conceptual clarity
- Internal workings
- Real-world backend relevance
- Common interviewer traps
