# 📘 `notes.md` — Lesson 3: JVM Memory Model (Stack vs Heap)

````md
# Lesson 3: JVM Memory Model (Stack vs Heap)

This note explains how memory is managed inside the JVM, focusing on the **stack and heap**, which is a core concept for backend development and multithreading.

---

## 1. JVM Memory Ownership

All memory in a Java application is **managed by the JVM**.

Developers do not allocate or free memory manually.  
The JVM divides memory into logical regions for safe and efficient execution.

---

## 2. Stack Memory

### What Stack Memory Is Used For
- Method calls
- Local variables
- Object references
- Control flow (method execution)

---

### Key Characteristics
- Thread-specific
- Follows LIFO (Last In, First Out)
- Very fast
- Automatically cleaned when methods return

Each thread has its **own stack**, ensuring isolation of execution.

---

### Example
```java
void methodA() {
    int x = 10;
    methodB();
}

void methodB() {
    int y = 20;
}
````

Each method call creates a **stack frame** that is pushed and popped during execution.

---

## 3. Heap Memory

### What Heap Memory Is Used For

* Objects
* Instance variables
* Shared application data

---

### Key Characteristics

* Shared across all threads
* Managed by Garbage Collector
* Slower than stack
* Objects live until they are no longer referenced

---

### Example

```java
Person p = new Person();
```

* Reference `p` → stack
* Object `Person` → heap

---

## 4. Stack vs Heap Comparison

| Stack                   | Heap                  |
| ----------------------- | --------------------- |
| Stores method execution | Stores objects        |
| Thread-specific         | Shared across threads |
| Faster                  | Slower                |
| Automatically cleaned   | Cleaned by GC         |
| Small                   | Large                 |

---

## 5. Common Misconception

❌ “Primitives are stored in stack, objects in heap”

✅ Correct understanding:

* Local variables (primitives & references) → stack
* Objects & instance variables → heap

---

## 6. Errors Related to Memory

### StackOverflowError

* Caused by excessive stack usage
* Commonly due to deep or infinite recursion

---

### OutOfMemoryError

* Heap memory is exhausted
* Objects are not released
* Often caused by memory leaks

---

## 7. Backend Relevance

* Stack memory is safe for execution
* Heap memory requires synchronization
* Understanding this helps debug:

  * Concurrency issues
  * Memory leaks
  * Performance problems

---