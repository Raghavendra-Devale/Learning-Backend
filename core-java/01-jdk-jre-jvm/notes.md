# 📘 Lesson 1: JDK vs JRE vs JVM

This note explains the difference between **JDK**, **JRE**, and **JVM**—a **foundational concept** for Java backend roles and a **frequent interview topic**.

A clear understanding here prevents many classic interview mistakes and helps later with debugging, deployment, and performance tuning.

---

## Big Picture (Before Details)

Java follows a **write once, run anywhere (mostly)** philosophy:

- You **write** code once
- You **compile** it into bytecode
- The **JVM** runs it on different systems

Keep this mental model active as you read.

---

## 1. JVM — Java Virtual Machine

### What is the JVM?
The **JVM** is a runtime engine that **executes Java bytecode** (`.class` files).

Java programs **never run directly on the operating system**.  
They always run *inside* a JVM.

---

### Responsibilities of the JVM

The JVM handles everything that happens **after compilation**:

- Class loading
- Bytecode verification
- Memory management (heap, stack, method area)
- Garbage collection
- Thread management
- Bytecode execution (interpreter + JIT compiler)

---

### Important JVM Facts

- JVM is **platform-dependent**
- JVM does **not compile** Java source code
- JVM executes **bytecode**, not `.java` files

Think of the JVM as the **bridge between Java and the OS**.

---

## 2. JRE — Java Runtime Environment

### What is the JRE?
The **JRE** provides everything required to **run** a Java application.

If you only want to *execute* Java programs, this is enough.

---

### What the JRE Contains

- JVM
- Core Java libraries  
  (`java.lang`, `java.util`, `java.io`, etc.)

---

### Key Notes About JRE

- Used only for **execution**
- Does **not include the compiler**
- Commonly installed on **production servers**

Production environments care about stability and security—not compilation.

---

## 3. JDK — Java Development Kit

### What is the JDK?
The **JDK** is used to **develop** Java applications.

This is what developers install on their machines.

---

### What the JDK Contains

- JRE
- Java compiler (`javac`)
- Debugger
- Development and diagnostic tools

---

### Key Notes About JDK

- Required to **compile** Java code
- Used during **development**
- Usually **not installed in production**

Development ≠ Deployment. This distinction matters in real systems.

---

## 4. Java Code Execution Flow

```text
.java  →  javac  →  .class (bytecode)  →  JVM  →  OS / Hardware
````

### Step-by-Step

1. Developer writes Java source code (`.java`)
2. `javac` compiles it into bytecode (`.class`)
3. JVM loads and verifies the bytecode
4. JVM executes it on the host system

---

## 5. Platform Independence Explained

* Java **source code** is platform independent
* Java **bytecode** runs on platform-specific JVMs
* JVM hides operating system differences

That’s why Java is *portable*, not magical.

---

## 6. One-Line Summary (Interview Gold)

* **Develop** → JDK
* **Run** → JRE
* **Execute** → JVM

If you freeze in an interview, this saves you.

---

## 7. Why This Matters for Backend Developers

Understanding JDK, JRE, and JVM helps with:

* Production setup decisions
* Debugging runtime issues
* Explaining deployment architecture
* JVM tuning and performance discussions

This topic keeps paying dividends as you grow.

---