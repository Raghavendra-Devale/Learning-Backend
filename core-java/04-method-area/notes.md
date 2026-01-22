
# 📘 `notes.md` — Lesson 4: Method Area & Metaspace

```md
# Lesson 4: Method Area & Metaspace

This note explains the **Method Area (Metaspace)** in the JVM and how it stores **class-level information**, including static variables.

---

## 1. What Is the Method Area?

The Method Area is a JVM memory region that stores **class-level data**, not object data.

It contains:
- Class metadata
- Method bytecode
- Static variables
- Runtime constant pool

---

## 2. Metaspace (Java 8+)

### Before Java 8
- Method Area implemented as **PermGen**
- Fixed size
- Frequent `OutOfMemoryError: PermGen space`

---

### Java 8 and Later
- Method Area implemented as **Metaspace**
- Uses native memory (outside heap)
- Grows dynamically

This change improved stability and reduced class-loading related memory errors.

---

## 3. Static vs Instance Variables

### Instance Variables
```java
class User {
    int age;
}
```

- Stored in **heap**
- Each object has its own copy

---

### Static Variables
```java
class Config {
    static int TIMEOUT = 30;
}
```

- Stored in **Method Area / Metaspace**
- One copy per class
- Shared across all threads and objects

---

## 4. Memory Layout Overview

```
Metaspace (Method Area)
 └── Class metadata
 └── Static variables

Heap
 └── Objects
    └── Instance variables

Stack (per thread)
 └── Method calls
 └── Local variables
```

---

## 5. Class Loading and Static Initialization

- Classes are loaded when first referenced
- Static variables are initialized during class loading
- Class metadata remains in Metaspace until class unloading

---

## 6. Backend Relevance

- Static data is shared globally within JVM
- Improper static usage can cause:
  - Thread-safety issues
  - Memory leaks
  - Unexpected behavior in multi-user systems

Frameworks like Spring avoid static state and manage shared objects safely using dependency injection.


