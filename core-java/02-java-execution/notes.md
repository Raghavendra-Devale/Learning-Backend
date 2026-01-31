# 📘 Lesson 2: How Java Code Executes Internally

This note explains the **internal execution flow of Java programs inside the JVM**.  
Interviewers use this topic to test whether you understand Java *beyond syntax*—at the runtime and JVM level.

---

## Big Picture First

Java source code **never runs directly on the operating system**.

Instead, execution happens through a controlled JVM pipeline designed for:
- safety
- portability
- performance

### High-Level Flow

```text
.java → compiler → .class (bytecode) → JVM → execution
````

The interesting part is **what happens inside the JVM**.

---

## 1. JVM Execution Pipeline

When a Java program starts, the JVM processes it in **three major stages**:

1. Class Loading
2. Bytecode Verification
3. Bytecode Execution (Interpreter + JIT)

Each stage exists for a reason—remove one, and Java breaks its guarantees.

---

## 2. Class Loading

### What Is Class Loading?

The JVM loads `.class` files **only when they are needed**.
This strategy is called **lazy loading**.

Classes are not loaded all at once at startup, which saves memory and improves startup time.

---

### ClassLoader Subsystem

The JVM uses a **hierarchy of class loaders**:

#### 1. Bootstrap ClassLoader

* Loads core Java classes
* Examples: `java.lang.Object`, `java.lang.String`
* Implemented in native (non-Java) code

#### 2. Extension ClassLoader

* Loads Java extension libraries

#### 3. Application ClassLoader

* Loads application-specific classes from the classpath

---

### Parent-First Delegation Model

Before a class is loaded:

1. Application ClassLoader asks the Extension ClassLoader
2. Extension ClassLoader asks the Bootstrap ClassLoader
3. The class is loaded only if no parent has it

This model ensures:

* core Java classes cannot be overridden
* consistent behavior across applications
* stronger runtime security

---

## 3. Bytecode Verification

### Why Verification Exists

Before execution, the JVM **verifies bytecode for safety**.

Java allows code from different sources to run together—verification prevents malicious or corrupted code from breaking the system.

---

### What the JVM Verifies

* Correct stack operations
* Type safety
* No illegal memory access
* No forged or corrupted bytecode

If verification fails, the program **does not execute**.

Fail fast > fail dangerously.

---

## 4. Bytecode Execution

Once bytecode passes verification, the JVM executes it using **two complementary mechanisms**.

---

### Interpreter

* Executes bytecode **instruction by instruction**
* Fast startup
* Slower execution
* Used at the beginning of program execution

The interpreter helps Java start quickly.

---

### JIT (Just-In-Time Compiler)

* Detects **frequently executed code** (hot code)
* Compiles bytecode into native machine code
* Caches compiled code for reuse
* Provides near-native performance

This is where Java gets fast.

---

## 5. Why JVM Uses Both Interpreter and JIT

Using only one would be inefficient.

* Interpreter → fast startup, slow execution
* JIT → slower startup, very fast execution

The JVM balances both:

* interpret first
* optimize later
* compile only what matters

This design is why Java performs well in long-running backend systems.

---

## 6. Backend Relevance

Understanding JVM execution helps you reason about:

* application warm-up time
* latency spikes after deployment
* performance tuning decisions
* JVM-related production issues

At scale, JVM behavior becomes *application behavior*.

---

## One-Sentence Mental Model

> “The JVM safely loads classes, verifies bytecode, and gradually optimizes execution using JIT for performance.”

---