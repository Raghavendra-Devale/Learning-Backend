# 🎯 Interview Questions: HashMap Internals

This document covers **internal working, performance characteristics, and design decisions** of `HashMap`, a frequently tested topic in Java backend interviews.

---

## 1. How does HashMap work internally?

### ✅ Answer
`HashMap` internally uses an **array of buckets**.

- `hashCode()` is used to determine the bucket index
- `equals()` is used to identify the correct key within the bucket

Each bucket can store multiple entries in case of collisions.

---

## 2. Why is HashMap capacity always a power of 2?

### ✅ Answer
Using a power-of-2 capacity allows fast bucket index calculation using **bitwise AND (`&`)** instead of modulo.

This improves performance and ensures better hash distribution.

---

## 3. What triggers resizing in HashMap?

### ✅ Answer
Resizing occurs when the number of entries exceeds:

```

capacity × loadFactor

```

The default load factor is **0.75**, balancing memory usage and performance.

---

## 4. How does HashMap handle collisions?

### ✅ Answer
- Initially, collisions are handled using **linked lists**
- In **Java 8 and later**, if a bucket becomes too large, it is converted into a **red-black tree**

This improves lookup performance in heavily-collided buckets.

---

## 5. Why was treeification introduced in Java 8?

### ✅ Answer
To improve worst-case performance.

- Linked list lookup → **O(n)**
- Tree-based lookup → **O(log n)**

Treeification protects HashMap from performance degradation due to poor hash distribution.

---

## 6. Is HashMap thread-safe?

### ❌ No.

### ✅ Correct Explanation
`HashMap` is **not thread-safe**.

Concurrent modifications can lead to:
- data inconsistency
- lost updates
- structural corruption

For concurrent access, alternatives like `ConcurrentHashMap` should be used.

---

## 7. What happens if two keys have the same `hashCode()`?

### ✅ Answer
Both keys are placed in the **same bucket**, and `equals()` is used to differentiate between them.

This is why both `hashCode()` and `equals()` must be implemented correctly.

---

## 🚫 Common Interview Traps & Pitfalls

- ❌ Saying HashMap avoids collisions  
- ❌ Saying resizing happens due to collisions  
- ❌ Assuming `hashCode()` is unique  
- ❌ Ignoring Java 8 treeification behavior  

---

## 🧠 One Interview-Safe Explanation

> “HashMap internally uses an array of buckets. It relies on `hashCode()` to locate a bucket and `equals()` to identify the correct key. Since Java 8, treeification is used to handle heavy collisions efficiently.”

---
```

---

### Mentor insight

If an interviewer pushes *one level deeper*, they usually go here next:

* **What happens during resize?**
* **Why mutable keys are dangerous**
* **Difference between HashMap and ConcurrentHashMap**