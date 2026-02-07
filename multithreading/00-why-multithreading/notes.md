# Multithreading – Level 0  
## Why Multithreading Exists

These notes explain the fundamental motivation behind multithreading, before diving into Java-specific APIs. This foundation is critical for understanding concurrency, synchronization, and performance in backend systems.

---

## 1. The Problem Before Multithreading

Early programs executed tasks sequentially.

Typical execution:
- Read data from disk or network
- Wait for I/O to complete
- Process data
- Wait again for output

During I/O operations:
- CPU remained idle
- System resources were wasted
- Programs felt slow and unresponsive

---

## 2. CPU Idle Time and I/O Wait

I/O operations (disk, network, user input) are much slower than CPU operations.

Without multithreading:
- A process blocks while waiting for I/O
- CPU does no useful work during this time

This led to poor performance and low throughput.

---

## 3. Core Idea of Multithreading

Multithreading allows a program to:
- Perform useful work while part of it is waiting
- Keep the CPU busy
- Improve responsiveness and throughput

**Key idea:**
> Do useful work while waiting for I/O.

---

## 4. What Is Multithreading?

Multithreading means:
- Multiple execution paths (threads)
- Running concurrently
- Inside the same process
- Sharing the same memory

Threads enable concurrency within a single application.

---

## 5. Multitasking vs Multithreading

### Multitasking
- OS-level concept
- Multiple processes
- Separate memory spaces

### Multithreading
- Application-level concept
- Multiple threads
- Shared memory

---

## 6. Why Threads Instead of Processes?

Processes are:
- Heavyweight
- Expensive to create
- Slow to communicate (IPC)

Threads are:
- Lightweight
- Share memory
- Faster to create and switch

This makes threads ideal for high-performance applications.

---

## 7. JVM and OS Relationship

- Java threads map to OS threads
- OS scheduler decides execution order
- Thread scheduling is non-deterministic

JVM manages memory and synchronization, but scheduling is handled by the OS.

---

## 8. The Cost of Shared Memory

Sharing memory allows:
- Fast communication
- Efficient data sharing

But introduces:
- Race conditions
- Data inconsistency
- Concurrency bugs

These problems are inherent to shared-memory systems.

---

## 9. Key Mental Model (Lock This)

- **Concurrency**: making progress on multiple tasks
- **Parallelism**: executing tasks at the same time

Multithreading enables concurrency and may enable parallelism on multi-core systems.

---

## 10. Interview-Safe Summary

> “Multithreading exists to improve CPU utilization and responsiveness by allowing a program to do useful work while waiting for I/O, using multiple execution paths within the same process.”

---
