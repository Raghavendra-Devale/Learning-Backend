---
title: Interview Questions – Method Area & Metaspace
lesson: 4
---

# 🎯 Interview Questions: Method Area & Metaspace

This file contains **frequently asked interview questions**, **common traps**, and **safe explanations** related to the JVM Method Area and Metaspace.

---

## 1. What is stored in the Method Area?

### ✅ Answer
The Method Area stores **class-level information**, including:
- class metadata
- method bytecode
- static variables
- runtime constant pool

---

## 2. What is Metaspace?

### ✅ Answer
Metaspace is the **Java 8+ implementation of the Method Area**.  
It uses **native memory** instead of heap memory and **grows dynamically**.

---

## 3. Why was PermGen removed?

### ✅ Answer
PermGen had a **fixed size**, which frequently caused  
`OutOfMemoryError: PermGen space`.

Metaspace removes this limitation by using **native memory** and allowing dynamic growth.

---

## 4. Where are static variables stored?

### ✅ Answer
Static variables are stored in the **Method Area**, which is implemented as **Metaspace** in Java 8 and later.

---

## 5. Why are static variables shared across threads?

### ✅ Answer
Static variables have **one copy per class**, and the class is shared across all threads inside the JVM.

---

## 6. Why is static state dangerous in backend applications?

### ✅ Answer
Static variables are **shared across threads and requests**, which can cause:
- race conditions
- inconsistent data
- hard-to-debug concurrency issues

---

## 7. How is a Spring singleton different from a static variable?

### ✅ Answer
A Spring singleton is **container-managed**, with controlled lifecycle and dependency injection.  
Static variables are **unmanaged global state** with no lifecycle or thread-safety guarantees.

---

## 🚫 Common Interview Traps & Pitfalls

- ❌ Saying static variables are stored in the heap
- ❌ Confusing heap memory with the Method Area
- ❌ Saying Metaspace is part of the Java heap
- ❌ Assuming static variables are thread-safe

---

## 🧠 One Interview-Safe Explanation

> “The Method Area stores class-level information like static variables and method bytecode. Since Java 8, it’s implemented using Metaspace, which uses native memory and grows dynamically.”

---
