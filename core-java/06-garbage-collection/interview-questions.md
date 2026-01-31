---
title: Interview Questions – Garbage Collection (GC)
lesson: 6
---

# 🎯 Interview Questions: Garbage Collection (GC)

This document covers **core garbage collection concepts**, **decision mechanisms**, and **performance implications**, commonly tested in Java backend interviews.

---

## 1. What is Garbage Collection in Java?

### ✅ Answer
Garbage Collection is a JVM process that **automatically reclaims heap memory** by removing objects that are no longer reachable.

It eliminates the need for manual memory deallocation.

---

## 2. How does the JVM decide which objects to collect?

### ✅ Answer
The JVM uses **reachability analysis**.

Objects that are **not reachable from any GC root** are eligible for garbage collection.

---

## 3. What are GC roots?

### ✅ Answer
GC roots are starting points for reachability analysis, including:
- active thread stacks (local variables)
- static variables
- JNI references

Objects reachable from GC roots are considered alive.

---

## 4. Why does the JVM use generational garbage collection?

### ✅ Answer
Because **most objects die young**.

By separating objects into generations, the JVM can:
- collect short-lived objects frequently
- reduce GC overhead
- improve overall performance

---

## 5. What is Stop-The-World (STW)?

### ✅ Answer
Stop-The-World is a GC phase during which **all application threads are paused** so the JVM can safely perform garbage collection.

Some GC algorithms minimize STW duration, but they cannot eliminate it completely.

---

## 6. What is the difference between Minor GC and Full GC?

### ✅ Answer
- **Minor GC** runs on the **Young Generation** and is usually fast
- **Full GC** runs on the **Old Generation**, is more expensive, and causes longer pauses

Full GC has a higher performance impact on backend applications.

---

## 7. Can `System.gc()` force garbage collection?

### ❌ No.

### ✅ Correct Explanation
`System.gc()` only **requests** garbage collection.  
The JVM decides **if and when** GC actually runs.

---

## 8. What causes GC performance issues in backend applications?

### ✅ Answer
Common causes include:
- excessive object creation
- large or long-lived objects
- static references holding memory
- improperly managed caches

High allocation rates increase GC pressure.

---

## 🚫 Common Interview Traps & Pitfalls

- ❌ Saying GC runs immediately when an object becomes unreachable
- ❌ Claiming GC is based on reference counting
- ❌ Saying `System.gc()` guarantees garbage collection
- ❌ Ignoring Stop-The-World pause impact

---

## 🧠 One Interview-Safe Explanation

> “Garbage Collection in Java automatically reclaims heap memory by removing unreachable objects. The JVM uses a generational approach to improve performance while managing pause times.”

---
