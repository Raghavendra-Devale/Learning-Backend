# Multithreading – Lesson 3  
## Thread Lifecycle & Thread States

These notes explain the lifecycle of a Java thread and the meaning of each thread state. This topic is frequently asked in interviews and is critical for debugging concurrency issues.

---

## 1. Thread Lifecycle Overview

A thread does not run continuously.
It moves through different states from creation to termination.

Java defines thread states using `Thread.State`.

---

## 2. NEW State

A thread is in NEW state when:
```java
Thread t = new Thread(task);
````

Characteristics:

* Thread object is created
* OS thread is NOT created yet
* Thread has not started execution

Creating a thread object does not start the thread.

---

## 3. RUNNABLE State

A thread enters RUNNABLE when:

```java
t.start();
```

What RUNNABLE means:

* Thread is ready to run OR
* Thread is currently running

Important:

* RUNNABLE does NOT mean running immediately
* OS scheduler decides when the thread actually runs

Thread scheduling is non-deterministic.

---

## 4. BLOCKED State

A thread enters BLOCKED state when:

* It tries to enter a synchronized block or method
* Another thread already holds the required lock

Key points:

* BLOCKED is always lock-related
* Thread waits until lock is released

---

## 5. WAITING State

A thread enters WAITING state when it waits indefinitely for another thread.

Common causes:

* `Object.wait()`
* `Thread.join()` (without timeout)

Characteristics:

* No CPU usage
* Thread waits until another thread signals it

---

## 6. TIMED_WAITING State

A thread enters TIMED_WAITING when it waits for a fixed amount of time.

Common causes:

* `Thread.sleep(time)`
* `Object.wait(time)`
* `Thread.join(time)`

Difference from WAITING:

* Automatically wakes after timeout

---

## 7. TERMINATED State

A thread enters TERMINATED state when:

* `run()` method completes
* OR an uncaught exception occurs

Characteristics:

* Thread is dead
* Cannot be restarted
* Calling `start()` again throws exception

---

## 8. BLOCKED vs WAITING (Very Important)

* BLOCKED → waiting for a lock
* WAITING → waiting for a signal/action from another thread

This distinction is a common interview question.

---

## 9. Backend Relevance

Understanding thread states helps:

* Debug hanging applications
* Identify deadlocks and lock contention
* Analyze thread dumps
* Write correct synchronization logic

---

## 10. Interview-Safe Summary

> “A Java thread moves through states like NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING, and TERMINATED. RUNNABLE does not guarantee execution, BLOCKED is lock-related, and WAITING is coordination-related.”

---
