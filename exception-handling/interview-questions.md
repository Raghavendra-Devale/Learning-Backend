# 📘 Exception Handling – Interview Question Index (By Experience Level)

This index organizes **exception-handling interview questions** based on **experience level and interviewer depth**.
Use this as a **revision guide** before interviews.

---

## 🟢 LEVEL 0 — Absolute Beginner / Academic / Professor-Level Basics

> Focus: **Concept clarity, definitions, fundamentals**

These are asked in:

* College viva
* First screening rounds
* Theory-heavy interviews

### Core Questions

1. What is an exception?
2. Why do exceptions occur?
3. Difference between error and exception?
4. What is the root class of all exceptions?
5. What are checked exceptions?
6. What are unchecked exceptions?
7. Give examples of checked exceptions.
8. Give examples of unchecked exceptions.
9. What is the purpose of try–catch?
10. What is finally block?
11. Does finally always execute?
12. What happens if an exception is not handled?

📌 **Expected depth**: Definitions + 1 example
📌 **Mistake to avoid**: Saying `Exception` is the root class (it is `Throwable`)

---

## 🟡 LEVEL 1 — Fresher / Junior Backend Developer (0–1 YOE)

> Focus: **Reasoning, design intent, correctness**

These are asked in:

* Fresher backend interviews
* Entry-level Java developer roles

### Core Questions

1. Difference between checked and unchecked exceptions?
2. Why does Java have checked exceptions?
3. When should you use checked exceptions?
4. Why are unchecked exceptions not forced to be handled?
5. What is exception propagation?
6. What happens when an exception is thrown inside a method?
7. Difference between throw and throws?
8. Can we catch multiple exceptions?
9. What is exception hierarchy?
10. What happens if finally has a return statement?
11. Should we catch `Exception`?
12. Why is swallowing exceptions dangerous?

📌 **Expected depth**: Explain *why*, not just *what*
📌 **Mistake to avoid**: Saying “all exceptions must be handled”

---

## 🟠 LEVEL 2 — Strong Fresher / 1–2 Years Experience

> Focus: **Best practices, pitfalls, API design**

These are asked in:

* Product companies
* Strong service-based companies
* Second technical rounds

### Core Questions

1. Difference between Error, Exception, and RuntimeException?
2. Why does RuntimeException exist?
3. Recoverable vs non-recoverable exceptions?
4. Should RuntimeException be caught?
5. When should you rethrow an exception?
6. What is exception wrapping?
7. Why should you preserve the original cause?
8. What is exception translation?
9. Where should exceptions be logged?
10. Why should exceptions be logged only once?
11. Why is using exceptions for control flow bad?
12. What does “fail fast” mean?
13. Give examples of fail-fast exceptions.
14. How do frameworks like Spring handle exceptions?

📌 **Expected depth**: Real backend reasoning
📌 **Mistake to avoid**: Logging exceptions in every layer

---

## 🔵 LEVEL 3 — 2–3 Years Experience (Backend / Guide Level)

> Focus: **System design, layering, production behavior**

These are asked in:

* Senior backend rounds
* Design-heavy interviews
* Lead / guide-style discussions

### Core Questions

1. How do you design exception handling in a layered application?
2. Why do modern frameworks prefer RuntimeException?
3. How do you avoid polluting method signatures with exceptions?
4. How do you map exceptions to HTTP responses?
5. Where should exception handling logic live?
6. What is global exception handling?
7. How does Spring handle exceptions internally?
8. What are common exception-handling anti-patterns?
9. How do you design custom exceptions?
10. Should DAO layer throw checked or unchecked exceptions?
11. How do you handle exceptions in async code?
12. How do you ensure exceptions don’t leak sensitive information?
13. What happens to unchecked exceptions in thread pools?
14. How does exception handling affect system observability?

📌 **Expected depth**: Architecture + production awareness
📌 **Mistake to avoid**: Saying “just catch in controller”

---

## 🔴 SENIOR / ARCHITECT FOLLOW-UP QUESTIONS (ANY LEVEL)

> These are **depth-check questions** used when interviewer wants to push you.

1. Why is catching `Throwable` a bad idea?
2. What happens if an exception is thrown in a constructor?
3. Can finally override an exception?
4. How do suppressed exceptions work?
5. Why are checked exceptions bad for functional programming?
6. How do exceptions behave in streams?
7. How does exception handling differ in synchronous vs async code?
8. How would you design exception handling for a microservice?
9. What is the cost of throwing exceptions?
10. How do you test exception paths?

📌 **Expected depth**: Calm, logical explanation
📌 **Mistake to avoid**: Over-theoretical answers

---

## 🧠 One-Minute Master Answer (Works at Any Level)

> “Java’s exception model separates unrecoverable system errors from application-level failures. Checked exceptions represent recoverable conditions, while RuntimeExceptions represent programming errors. In real backend systems, exceptions are translated across layers, logged once at boundaries, and mapped to meaningful responses.”

---

## ✅ How to Use This Index

* **Freshers** → Master Level 0 & 1
* **1–2 YOE** → Level 2 + traps
* **2–3 YOE** → Level 3 + senior follow-ups
* **Before interview** → Read only this index + interview-questions.md

---
