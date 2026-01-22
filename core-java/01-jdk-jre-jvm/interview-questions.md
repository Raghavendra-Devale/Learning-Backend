
---

# 🎯 `interview-questions.md` — Lesson 1

```md
# Interview Questions – JDK vs JRE vs JVM

This file contains **important interview questions, traps, and pitfalls** related to JDK, JRE, and JVM.

---

## Q1. What is the difference between JDK, JRE, and JVM?

### Answer:
JDK is used to develop Java applications and includes the compiler.  
JRE provides the runtime environment to run Java programs.  
JVM executes the bytecode and manages memory, threads, and execution.

---

## Q2. Can we run Java code without JDK?

### Correct Answer:
Yes. Java applications can be run using only the JRE.

### Interview Trap:
Many candidates incorrectly say JDK is required to run Java programs.

---

## Q3. Does JVM compile Java code?

### Answer:
No. Java code is compiled by `javac`, which is part of the JDK.  
JVM only executes bytecode.

---

## Q4. Is Java completely platform independent?

### Correct Answer:
Java source code is platform independent, but bytecode runs on platform-specific JVM implementations.

---

## Q5. Why is JVM platform dependent?

### Answer:
Because JVM interacts directly with the operating system and hardware, and different platforms require different JVM implementations.

---

## Q6. What is bytecode?

### Answer:
Bytecode is an intermediate representation of Java source code that is executed by the JVM.

---

## Q7. Why don’t production servers install JDK?

### Answer:
Production servers only need to run Java applications, so JRE is sufficient.  
Installing JDK increases attack surface and is unnecessary.

---

## Q8. What happens if JVM is not present on a system?

### Answer:
Java bytecode cannot be executed because JVM is required to run Java programs.

---

## Common Pitfalls to Avoid

❌ Saying Java runs directly on OS  
❌ Saying JVM compiles Java code  
❌ Saying JDK is required to run Java programs  
❌ Saying Java is 100% platform independent  

---

## One Interview-Safe Statement

> “JDK is used for development, JRE is used for running Java applications, and JVM is responsible for executing bytecode and managing runtime behavior.”

---
````