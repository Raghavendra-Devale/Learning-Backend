# 🎯 `interview-questions.md` — Lesson 3

# Interview Questions – JVM Stack vs Heap

---

## Q1. What is the difference between stack and heap memory?

### Answer:
Stack memory is used for method execution and local variables and is thread-specific, while heap memory stores objects and is shared across threads.

---

## Q2. Why is stack memory thread-safe?

### Answer:
Each thread has its own stack, so method execution and local variables are isolated from other threads.

---

## Q3. Why does heap memory require synchronization?

### Answer:
Heap memory is shared across threads, so concurrent access can lead to race conditions without proper synchronization.

---

## Q4. Where are object references stored?

### Answer:
Object references are stored where the variable is declared (stack for local variables, heap for instance variables), while the actual object is stored in heap memory.

---

## Q5. What causes StackOverflowError?

### Answer:
StackOverflowError occurs when the call stack exceeds its limit, usually due to deep or infinite recursion.

---

## Q6. What causes OutOfMemoryError?

### Answer:
OutOfMemoryError occurs when the heap memory is exhausted and the JVM cannot allocate more objects.

---

## Common Interview Traps & Pitfalls

❌ Saying primitives are always stored in stack  
❌ Saying heap memory is thread-safe  
❌ Confusing StackOverflowError with OutOfMemoryError  
❌ Saying JVM does not manage memory  

---

## One Interview-Safe Explanation

> “Stack memory is thread-specific and used for method execution, while heap memory is shared across threads and stores objects, which is why concurrency issues arise in heap memory.”

---
