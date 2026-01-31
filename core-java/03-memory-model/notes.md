# 📘 Lesson 3: JVM Memory Model (Stack vs Heap)

This note explains how memory is managed inside the JVM, with a focus on the **Stack** and **Heap**—a core concept for backend development, multithreading, and performance analysis.

---

## Big Picture First

All memory in a Java application is **managed by the JVM**.

Developers do not manually allocate or free memory.  
Instead, the JVM divides memory into **logical regions**, each with a clear purpose and lifecycle.

Two of the most important regions are:
- Stack → execution
- Heap → data

---

## 1. Stack Memory

### What Stack Memory Is Used For

Stack memory supports **method execution**.  
It stores:

- Method call information
- Local variables
- Object references
- Control flow (which method is currently running)

---

### Key Characteristics of Stack Memory

- **Thread-specific** (each thread has its own stack)
- Follows **LIFO** (Last In, First Out)
- Extremely **fast**
- Automatically cleaned when a method returns

Because stacks are isolated per thread, stack memory is **inherently thread-safe**.

---

### Example: Stack Frames in Action

```java
void methodA() {
    int x = 10;
    methodB();
}

void methodB() {
    int y = 20;
}
````

Execution behavior:

* `methodA()` creates a stack frame
* `methodB()` creates a new stack frame on top
* `methodB()` finishes → its frame is popped
* `methodA()` finishes → its frame is popped

Stack frames exist **only for the duration of method execution**.

---

## 2. Heap Memory

### What Heap Memory Is Used For

Heap memory stores **objects and shared application data**, including:

* Objects
* Instance variables
* Data shared across threads

---

### Key Characteristics of Heap Memory

* **Shared across all threads**
* Managed by the **Garbage Collector**
* Slower than stack access
* Objects live as long as they are reachable

Heap memory represents the **state of the application**.

---

### Example: Reference vs Object

```java
Person p = new Person();
```

Memory behavior:

* Reference variable `p` → stored in the **stack**
* `Person` object → stored in the **heap**

The stack knows *where* the object is.
The heap stores *what* the object is.

---

## 3. Stack vs Heap — Clear Comparison

| Stack                   | Heap                         |
| ----------------------- | ---------------------------- |
| Stores method execution | Stores objects and data      |
| Thread-specific         | Shared across threads        |
| Very fast               | Slower than stack            |
| Auto-cleaned on return  | Cleaned by Garbage Collector |
| Small, fixed per thread | Large, dynamically managed   |

---

## 4. Common Misconception (Very Important)

❌ “Primitives are stored in stack, objects are stored in heap”

This is **incomplete and misleading**.

### ✅ Correct Mental Model

* Local variables (primitives **and references**) → stack
* Objects and their instance variables → heap

What matters is **scope and lifetime**, not data type.

---

## 5. Memory-Related Errors

### StackOverflowError

* Caused by excessive stack usage
* Common reasons:

  * deep recursion
  * infinite recursion
  * too many nested method calls

Each recursive call adds a new stack frame.

---

### OutOfMemoryError (Heap)

* Heap memory is exhausted
* Objects are not eligible for garbage collection
* Often caused by:

  * memory leaks
  * unbounded collections
  * long-lived object references

---

## 6. Backend Relevance

Understanding stack vs heap helps you reason about:

* thread safety
* synchronization requirements
* memory leaks
* performance bottlenecks

### Practical Rule of Thumb

* Stack → execution, safe, short-lived
* Heap → shared state, powerful, dangerous if misused

---

## One-Line Interview Summary

> “The stack stores method execution and local variables per thread, while the heap stores objects shared across threads and is managed by the garbage collector.”

---