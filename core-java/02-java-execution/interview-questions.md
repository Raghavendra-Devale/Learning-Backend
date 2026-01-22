# Interview Questions – Java Execution Internals

This file contains important interview questions, traps, and pitfalls related to Java execution inside the JVM.

---

## Q1. What happens internally when a Java program runs?

### Answer:
The JVM loads required classes, verifies bytecode for safety, and executes it using an interpreter. Frequently executed code paths are optimized by the JIT compiler.

---

## Q2. What is class loading in Java?

### Answer:
Class loading is the process of loading class files into memory when they are required during execution.

---

## Q3. What is the parent-first delegation model?

### Answer:
In the parent-first delegation model, a class loader delegates class loading to its parent before attempting to load the class itself, ensuring security and consistency.

---

## Q4. Why is bytecode verification required?

### Answer:
Bytecode verification ensures type safety, correct stack behavior, and prevents illegal memory access, protecting the JVM from malicious or corrupted code.

---

## Q5. Does JVM only interpret code?

### Answer:
No. JVM uses both an interpreter and a JIT compiler to execute bytecode efficiently.

---

## Q6. Why doesn’t JVM use JIT for all code immediately?

### Answer:
JIT compilation is expensive and unnecessary for code that executes infrequently, so JVM optimizes only frequently executed code.

---

## Q7. Why does Java performance improve over time?

### Answer:
Because the JIT compiler converts frequently executed bytecode into optimized native machine code.

---

## Common Interview Traps & Pitfalls

❌ Saying JVM loads all classes at startup  
❌ Saying JVM only interprets code  
❌ Saying JIT replaces interpreter completely  
❌ Ignoring bytecode verification step  

---

## One Interview-Safe Explanation

> “The JVM loads classes on demand, verifies bytecode for safety, and executes it using an interpreter. Frequently used code paths are optimized by the JIT compiler into native code.”

---
