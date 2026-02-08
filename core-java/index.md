# ☕ Core Java — Complete Notes & Interview Prep

This section contains **interview-focused Core Java notes**, covering JVM internals,
memory management, object lifecycle, and object-oriented design fundamentals.

The content is structured topic-wise so each concept can be revised independently
and confidently before interviews — including **indirect and twisted questions**.

---

## ✅ Core Java — Status

**Level Covered:** Strong Fresher → Junior Backend (0–2 YOE)

This section is sufficient for:
- Java fresher interviews
- Junior backend roles
- Handling indirect / twisted Core Java questions
- Confident explanation of JVM, memory, and OOPS design concepts

---

## 🗂 Core Java Index

### 01. JDK, JRE & JVM Basics
📁 Folder: `01-jdk-jre-jvm`

**Concepts**
- Role of JDK, JRE, JVM
- Java execution overview
- Platform independence (myths vs facts)
- High-level JVM architecture

- 📘 [Notes](./01-jdk-jre-jvm/notes.md)
- 🎯 [Interview Questions](./01-jdk-jre-jvm/interview-questions.md)

---

### 02. Java Execution Flow
📁 Folder: `02-java-execution`

**Concepts**
- Source code → bytecode → execution
- `javac`, bytecode, JVM role
- Why Java does not run directly on OS

- 📘 [Notes](./02-java-execution/notes.md)
- 🎯 [Interview Questions](./02-java-execution/interview-questions.md)

---

### 03. JVM Memory Model (Stack & Heap)
📁 Folder: `03-memory-model`

**Concepts**
- Stack vs Heap
- Thread stack isolation
- Stack frames & method calls
- StackOverflowError
- Heap sharing & concurrency impact

- 📘 [Notes](./03-memory-model/notes.md)
- 🎯 [Interview Questions](./03-memory-model/interview-questions.md)

---

### 04. Method Area & Metaspace
📁 Folder: `04-method-area`

**Concepts**
- Method Area responsibilities
- Class-level metadata
- Static variables & methods
- Why Metaspace replaced PermGen
- Thread-safety implications

- 📘 [Notes](./04-method-area/notes.md)
- 🎯 [Interview Questions](./04-method-area/interview-questions.md)

---

### 05. Object Creation & Lifecycle
📁 Folder: `05-object-creation`

**Concepts**
- `new` keyword internals
- Memory allocation steps
- Constructor execution order
- Object reachability
- GC eligibility basics

- 📘 [Notes](./05-object-creation/notes.md)
- 🎯 [Interview Questions](./05-object-creation/interview-questions.md)

---

### 06. Garbage Collection (GC)
📁 Folder: `06-garbage-collection`

**Concepts**
- What GC does and does not do
- Reachable vs unreachable objects
- Stop-The-World (STW)
- GC overhead & performance impact
- `System.gc()` reality

- 📘 [Notes](./06-garbage-collection/notes.md)
- 🎯 [Interview Questions](./06-garbage-collection/interview-questions.md)

---

### 07. OOPS Fundamentals & Design Concepts
📁 Folder: `07-oops-basics`

**Concepts**
- Abstraction, Encapsulation, Inheritance, Polymorphism
- Tight vs loose coupling
- Association, Aggregation, Composition
- Favor composition over inheritance
- Real backend design implications

- 📘 [Notes](./07-oops-basics/notes.md)
- 🎯 [Interview Questions](./07-oops-basics/interview-questions.md)

---

### 08. `equals()` & `hashCode()` Contract
📁 Folder: `08-equals-hashcode`

**Concepts**
- `equals()` vs `==`
- `hashCode()` contract
- Hash-based collection behavior
- Common bugs & interview traps

- 📘 [Notes](./08-equals-hashcode/notes.md)
- 🎯 [Interview Questions](./08-equals-hashcode/interview-questions.md)

---

### 09. Immutability & Defensive Copying
📁 Folder: `09-immutability`

**Concepts**
- What immutability really means
- `final` vs immutable
- Defensive copying (constructor & getters)
- Why `String` is immutable
- Backend usage scenarios

- 📘 [Notes](./09-immutability/notes.md)
- 🎯 [Interview Questions](./09-immutability/interview-questions.md)

---

### 10. Java Memory Leaks & References
📁 Folder: `10-memory-leaks`

**Concepts**
- Why Java can have memory leaks
- GC Roots
- Static & collection-based leaks
- ThreadLocal memory leaks
- WeakReference & WeakHashMap

- 📘 [Notes](./10-memory-leaks/notes.md)
- 🎯 [Interview Questions](./10-memory-leaks/interview-questions.md)

---

### 11. Serialization & Deserialization
📁 Folder: `11-serialization`

**Concepts**
- Java serialization mechanism
- Why constructors are not called
- `serialVersionUID`
- `transient` keyword
- Security risks & best practices

- 📘 [Notes](./11-serialization/notes.md)
- 🎯 [Interview Questions](./11-serialization/interview-questions.md)

---

### 12. Object Copying (Shallow vs Deep)
📁 Folder: `12-copying`

**Concepts**
- Assignment vs copy
- Shallow vs deep copy
- Why `clone()` is dangerous
- Copy constructors
- Backend pitfalls

- 📘 [Notes](./12-copying/notes.md)
- 🎯 [Interview Questions](./12-copying/interview-questions.md)

---

## 🧠 Twisted / Indirect Questions (Core Java)

📁 Folder: `twisted-questions/`

This section is designed to handle **indirect, tricky, and design-oriented questions**
asked by experienced interviewers.

**Covers**
- JVM & memory traps
- Stack vs heap trick questions
- GC myths
- OOPS design twists
- Coupling & composition traps
- equals/hashCode edge cases
- Serialization & cloning pitfalls

- 🧠 [Twisted Core Java Questions](./twisted-questions/core-java-twisted.md)
- 🧠 [OOPS Twisted Questions](./twisted-questions/oops-twisted.md)

---

## 🎯 How to Revise Core Java (Interview Mode)

1. Start with `interview-questions.md`
2. Use `notes.md` only for clarification
3. Before interviews:
   - Read **Twisted Questions**
   - Focus on “why”, not syntax
4. Practice explaining concepts verbally

---

## 🧠 Author’s Note

This Core Java section focuses on:
- JVM and memory reasoning
- Design thinking over memorization
- Handling indirect and twisted interview questions
- Backend-relevant explanations

This file is the **single entry point** for Core Java revision.

---
