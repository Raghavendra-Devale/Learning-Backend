# ⚠️ Java Exception Handling — Complete Notes & Interview Prep

This section contains **end-to-end, interview-focused exception handling notes**, covering
fundamentals, design philosophy, and real-world backend best practices.

The content is structured lesson-wise so each topic can be revised independently
based on **experience level (fresher → 2–3 YOE)**.

---

## ⚠️ Exception Handling Index

### 01. Fundamentals & Philosophy

**Concepts**
- Why exceptions exist
- Error vs Exception
- Checked vs unchecked exceptions
- try–catch–finally semantics
- Exception propagation
- Why swallowing exceptions is dangerous

- 📘 [Notes](./01-fundamentals/notes.md)
- 🎯 [Interview Questions](./01-fundamentals/interview-questions.md)

---

### 02. Exception Hierarchy & RuntimeException Design

**Concepts**
- `Throwable` as the root class
- Error vs Exception vs RuntimeException
- Why RuntimeException exists
- Recoverable vs non-recoverable failures
- Modern backend exception philosophy
- Where exceptions should be caught

- 📘 [Notes](./02-exception-hierarchy/notes.md)
- 🎯 [Interview Questions](./02-exception-hierarchy/interview-questions.md)

---

### 03. Custom Exceptions & Best Practices

**Concepts**
- Why custom exceptions are needed
- Checked vs unchecked custom exceptions
- Exception wrapping & preserving root cause
- Exception translation across layers
- Logging exceptions correctly (log once)
- Fail-fast principle
- Why exceptions should not be used for control flow

- 📘 [Notes](./03-custom-exceptions/notes.md)
- 🎯 [Interview Questions](./03-custom-exceptions/interview-questions.md)

---

## 🎯 How to Use This for Interviews

- **0 Level / Freshers**
  - Lesson 01 (complete)
  - Basic understanding of Lesson 02

- **1–2 YOE**
  - Lesson 01 + Lesson 02 (complete)
  - Key practices from Lesson 03

- **2–3 YOE**
  - All lessons
  - Focus on:
    - RuntimeException philosophy
    - Exception translation
    - Logging strategy
    - Fail-fast design

- **Before interview**
  - Read only `interview-questions.md` from each lesson

---

## 🧠 Author’s Note

These notes were created while preparing for **Java Backend interviews**, with focus on:
- Conceptual clarity over syntax
- Design intent behind Java exceptions
- Real backend and Spring-style practices
- Common interviewer traps and anti-patterns

This section is designed to help you **explain exceptions confidently**, not just write try–catch blocks.

---
