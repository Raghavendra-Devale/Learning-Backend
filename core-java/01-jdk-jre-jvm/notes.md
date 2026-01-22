
---

# 📘 `notes.md` — Lesson 1: JDK vs JRE vs JVM

````md
# Lesson 1: JDK vs JRE vs JVM

This note explains the difference between **JDK, JRE, and JVM**, which is a **fundamental and frequently asked interview topic** in Java backend roles.

Understanding this clearly avoids many common interview mistakes.

---

## 1. JVM (Java Virtual Machine)

### What is JVM?
The **JVM** is a runtime engine that **executes Java bytecode**.

Java programs never run directly on the operating system.  
They run inside the JVM.

---

### Responsibilities of JVM
- Loads classes
- Verifies bytecode
- Manages memory (heap, stack, method area)
- Handles garbage collection
- Manages threads
- Executes bytecode using interpreter and JIT compiler

---

### Important Points
- JVM is **platform-dependent**
- JVM does **not compile** Java code
- JVM executes `.class` files

---

## 2. JRE (Java Runtime Environment)

### What is JRE?
The **JRE** provides the environment required to **run Java applications**.

---

### JRE Includes
- JVM
- Core Java libraries (`java.lang`, `java.util`, etc.)

---

### Key Notes
- JRE is used only for **execution**
- JRE does **not include the compiler**
- Production servers usually need **only JRE**

---

## 3. JDK (Java Development Kit)

### What is JDK?
The **JDK** is used for **developing Java applications**.

---

### JDK Includes
- JRE
- Java compiler (`javac`)
- Debugger
- Development tools

---

### Key Notes
- Developers install **JDK**
- JDK is required to **compile** Java code
- JDK is not required in production environments

---

## 4. Code Execution Flow

```text
.java → javac → .class → JVM → OS
````

### Explanation

1. Java source code is compiled by `javac`
2. Compiler produces bytecode (`.class`)
3. JVM loads and verifies bytecode
4. JVM executes bytecode

---

## 5. Platform Independence

* Java source code is **platform independent**
* Bytecode runs on **platform-specific JVM**
* JVM hides OS-level differences

---

## 6. One-Line Summary (Must Remember)

* **Develop** → JDK
* **Run** → JRE
* **Execute** → JVM

---

## 7. Backend Relevance

Understanding JDK, JRE, and JVM helps in:

* Production setup decisions
* Debugging runtime issues
* Explaining deployment architecture
* JVM tuning and performance discussions

---

````
