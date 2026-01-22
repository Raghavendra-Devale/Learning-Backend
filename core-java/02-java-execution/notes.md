# Lesson 2: How Java Code Executes Internally

This note explains the **internal execution flow of Java programs inside the JVM**, a topic frequently used by interviewers to test JVM-level understanding.

---

## 1. Java Execution Overview

Java source code does not run directly on the operating system.

Execution flow:

.java → compiler → .class → JVM → execution

The JVM performs multiple internal steps before executing bytecode.

---

## 2. JVM Execution Pipeline

When a Java program runs, the JVM performs:

1. Class Loading  
2. Bytecode Verification  
3. Execution (Interpreter + JIT)

---

## 3. Class Loading

### What is Class Loading?
The JVM loads class files **only when they are required**, known as **lazy loading**.

---

### ClassLoader Subsystem

There are three main class loaders:

#### 1. Bootstrap ClassLoader
- Loads core Java classes
- Examples: `java.lang.String`, `java.lang.Object`
- Implemented in native code

#### 2. Extension ClassLoader
- Loads extension libraries

#### 3. Application ClassLoader
- Loads application-specific classes

---

### Parent-First Delegation Model

Before loading a class:
1. Application ClassLoader asks Extension ClassLoader
2. Extension asks Bootstrap ClassLoader
3. Class is loaded only if parent does not have it

This ensures:
- Security
- No overriding of core Java classes
- Stable runtime behavior

---

## 4. Bytecode Verification

### What is Bytecode Verification?
Before execution, JVM verifies bytecode to ensure safety.

---

### What JVM Verifies
- Correct stack usage
- Type safety
- No illegal memory access
- No corrupted or forged bytecode

If verification fails, execution is stopped.

---

## 5. Bytecode Execution

Java bytecode is executed using **two mechanisms**:

### Interpreter
- Executes bytecode line by line
- Slower
- Used initially

---

### JIT (Just-In-Time Compiler)
- Identifies frequently executed code (hot code)
- Compiles bytecode to native machine code
- Caches compiled code
- Provides high performance

---

## 6. Why JVM Uses Both Interpreter and JIT

- Interpreter provides fast startup
- JIT improves performance over time
- Not all code needs compilation

This balance makes Java efficient for backend systems.

---

## 7. Backend Relevance

Understanding JVM execution helps with:
- Application warm-up analysis
- Performance tuning
- JVM troubleshooting
- Explaining latency behavior in production systems

---
