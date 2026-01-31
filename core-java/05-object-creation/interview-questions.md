---
title: Interview Questions – Object Creation & Lifecycle
lesson: 5
---

# 🎯 Interview Questions: Object Creation & Lifecycle

This document covers **object creation, initialization, reachability, and garbage collection**, with a focus on how the JVM manages an object’s lifecycle.

---

## 1. What happens internally when we create an object using `new`?

### ✅ Answer
When `new` is used, the JVM:
1. Loads the class (if not already loaded)
2. Allocates memory for the object in the heap
3. Initializes instance variables with default values
4. Executes the constructor
5. Returns a reference to the object

---

## 2. Does the constructor allocate memory?

### ❌ No.
Memory allocation happens **before** the constructor runs.

### ✅ Correct Explanation
The JVM allocates memory for the object, then the constructor initializes that memory.

---

## 3. Where are objects stored in Java?

### ✅ Answer
Objects are stored in **heap memory**.

Only the reference to the object may exist in stack memory.

---

## 4. Where are methods stored?

### ✅ Answer
Method bytecode is stored in the **Method Area**, which is implemented as **Metaspace** in Java 8 and later.

Methods are **not stored inside objects**.

---

## 5. When does an object become eligible for garbage collection?

### ✅ Answer
An object becomes eligible for garbage collection when it is **no longer reachable** from any live thread.

Reachability, not scope, determines object lifetime.

---

## 6. Does garbage collection run immediately after an object becomes unreachable?

### ❌ No.

### ✅ Correct Explanation
Garbage collection runs **when the JVM decides**, based on memory pressure and GC algorithms—not immediately when an object becomes unreachable.

---

## 7. Can an object exist without any reference?

### ✅ Answer
Yes. An object can exist without any references, but it becomes **immediately eligible for garbage collection**.

Eligibility does not guarantee immediate collection.

---

## 8. What causes memory leaks in Java?

### ✅ Answer
Memory leaks occur when objects remain **reachable unintentionally**, commonly due to:
- static references
- long-lived objects holding short-lived references
- improperly managed caches or collections

The garbage collector can only collect *unreachable* objects.

---

## 🚫 Common Interview Traps & Pitfalls

- ❌ Saying the constructor allocates memory
- ❌ Saying objects are destroyed immediately when references are removed
- ❌ Confusing variable scope with object reachability
- ❌ Saying methods are stored in heap memory

---

## 🧠 One Interview-Safe Explanation

> “When `new` is used, the JVM allocates memory in the heap, initializes default values, executes the constructor, and returns a reference. Objects become eligible for garbage collection when they are no longer reachable.”

---
