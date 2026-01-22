

# 🎯 `interview-questions.md` — Lesson 4

```md
# Interview Questions – Method Area & Metaspace

---

## Q1. What is stored in the Method Area?

### Answer:
The Method Area stores class-level information such as class metadata, method bytecode, static variables, and the runtime constant pool.

---

## Q2. What is Metaspace?

### Answer:
Metaspace is the implementation of the Method Area in Java 8 and later, which uses native memory and grows dynamically.

---

## Q3. Why was PermGen removed?

### Answer:
PermGen had a fixed size and caused frequent OutOfMemoryErrors. Metaspace uses native memory and allows dynamic growth.

---

## Q4. Where are static variables stored?

### Answer:
Static variables are stored in the Method Area (Metaspace).

---

## Q5. Why are static variables shared across threads?

### Answer:
Static variables have one copy per class, and all threads access the same class-level data.

---

## Q6. Why is static state dangerous in backend applications?

### Answer:
Because static variables are shared across threads and requests, they can lead to race conditions, inconsistent data, and concurrency issues.

---

## Q7. How is a Spring singleton different from a static variable?

### Answer:
A Spring singleton is managed by the container with lifecycle control, while static variables are unmanaged global state.

---

## Common Interview Traps & Pitfalls

❌ Saying static variables are stored in heap  
❌ Confusing heap with Method Area  
❌ Saying Metaspace is part of heap  
❌ Treating static variables as thread-safe  

---

## One Interview-Safe Explanation

> “The Method Area stores class-level information such as static variables and method bytecode. In Java 8+, this is implemented using Metaspace, which uses native memory and grows dynamically.”

