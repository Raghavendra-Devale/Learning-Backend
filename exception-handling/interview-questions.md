

# 📘 Exception Handling — Interview Answers (With Explanations)


# 🟢 LEVEL 0 — Fundamentals

---

## 1. What is an exception?

**Answer:**
An exception is an event that disrupts the normal flow of program execution.

**Explanation:**
Instead of failing silently, Java creates an exception object to signal that something unexpected happened, allowing the program to handle or propagate the failure.

---

## 2. Why do exceptions occur?

**Answer:**
They occur due to invalid operations, external failures, or programming mistakes.

**Explanation:**
Examples include file access failure, invalid input, or accessing null references. Exceptions separate error handling from normal logic.

---

## 3. Difference between Error and Exception?

**Answer:**
Errors represent unrecoverable JVM problems, while exceptions represent application-level issues.

**Explanation:**
Errors indicate system failure (memory, JVM state). Exceptions allow controlled handling or recovery.

---

## 4. What is the root class of all exceptions?

**Answer:**
`Throwable`.

**Explanation:**
Both `Error` and `Exception` inherit from `Throwable`, which allows them to be thrown and caught.

---

## 5. What are checked exceptions?

**Answer:**
Exceptions enforced by the compiler that must be handled or declared.

**Explanation:**
They represent recoverable situations such as IO or database failures.

---

## 6. What are unchecked exceptions?

**Answer:**
Runtime exceptions not checked at compile time.

**Explanation:**
They usually indicate programming mistakes like null access or invalid indexing.

---

## 7. Examples of checked exceptions?

**Answer:**
`IOException`, `SQLException`, `ClassNotFoundException`.

**Explanation:**
These arise from external systems where recovery may be possible.

---

## 8. Examples of unchecked exceptions?

**Answer:**
`NullPointerException`, `IllegalArgumentException`, `IndexOutOfBoundsException`.

**Explanation:**
These typically result from incorrect code logic.

---

## 9. Purpose of try–catch?

**Answer:**
To handle exceptions and prevent abrupt program termination.

**Explanation:**
It allows recovery, logging, or translation of failures.

---

## 10. What is finally block?

**Answer:**
A block that executes cleanup code regardless of exceptions.

**Explanation:**
Used for releasing resources like files or database connections.

---

## 11. Does finally always execute?

**Answer:**
Almost always.

**Explanation:**
It may not execute during JVM crash or `System.exit()`.

---

## 12. What happens if an exception is not handled?

**Answer:**
It propagates up the call stack and may terminate the program.

**Explanation:**
This process is called stack unwinding.

---

# 🟡 LEVEL 1 — Junior Backend (0–1 YOE)

---

## 13. Checked vs unchecked exceptions?

**Answer:**
Checked exceptions represent recoverable failures; unchecked exceptions represent programming errors.

**Explanation:**
Compiler enforcement ensures recoverable problems are consciously handled.

---

## 14. Why does Java have checked exceptions?

**Answer:**
To force explicit handling of recoverable failures.

**Explanation:**
It prevents developers from ignoring important failure scenarios.

---

## 15. When should checked exceptions be used?

**Answer:**
When callers can recover from failure.

**Explanation:**
Typical at IO, network, or database boundaries.

---

## 16. Why aren’t unchecked exceptions forced to be handled?

**Answer:**
Because they represent bugs.

**Explanation:**
Forcing handling would encourage hiding errors instead of fixing them.

---

## 17. What is exception propagation?

**Answer:**
Passing an exception up the call stack until handled.

**Explanation:**
Each caller decides whether to handle or propagate further.

---

## 18. Difference between throw and throws?

**Answer:**
`throw` creates an exception; `throws` declares possible exceptions.

**Explanation:**
`throw` is used inside a method; `throws` appears in method signatures.

---

## 19. Can multiple exceptions be caught?

**Answer:**
Yes, using multiple catch blocks or multi-catch.

**Explanation:**
Java allows handling related exceptions together.

---

## 20. Should we catch Exception?

**Answer:**
Generally no.

**Explanation:**
It hides specific failures and reduces debugging clarity.

---

## 21. Why is swallowing exceptions dangerous?

**Answer:**
It hides failures and breaks debugging.

**Explanation:**
The system may continue in an inconsistent state.

---

# 🟠 LEVEL 2 — Strong Fresher (1–2 YOE)

---

## 22. Difference between Error, Exception, RuntimeException?

**Answer:**
Error → system failure
Exception → recoverable issue
RuntimeException → programming bug

**Explanation:**
This hierarchy defines responsibility for handling failures.

---

## 23. Why does RuntimeException exist?

**Answer:**
To represent bugs that should fail fast.

**Explanation:**
Mandatory handling would encourage meaningless try–catch blocks.

---

## 24. Should RuntimeException be caught?

**Answer:**
Usually no.

**Explanation:**
Fix the root cause unless adding context or translation.

---

## 25. What is exception wrapping?

**Answer:**
Rethrowing a higher-level exception while preserving the original cause.

**Explanation:**
Adds context without losing debugging information.

---

## 26. Why preserve the original cause?

**Answer:**
To retain the real failure source.

**Explanation:**
Without it, debugging becomes extremely difficult.

---

## 27. What is exception translation?

**Answer:**
Converting technical exceptions into business exceptions.

**Explanation:**
Prevents leaking implementation details across layers.

---

## 28. Where should exceptions be logged?

**Answer:**
At handling boundaries.

**Explanation:**
Usually controllers or global handlers.

---

## 29. Why log only once?

**Answer:**
To avoid duplicate stack traces.

**Explanation:**
Multiple logs create noise in monitoring systems.

---

## 30. Why not use exceptions for control flow?

**Answer:**
They are expensive and reduce readability.

**Explanation:**
Exceptions represent abnormal situations, not expected logic.

---

## 31. What does fail fast mean?

**Answer:**
Throw exceptions immediately when invalid input or state is detected.

**Explanation:**
Prevents corrupted state from spreading.

---

# 🔵 LEVEL 3 — Backend Engineer (2–3 YOE)

---

## 32. How do you design exception handling in layered architecture?

**Answer:**
Lower layers throw, service layers translate, boundary layers handle.

**Explanation:**
Keeps business logic clean and responsibilities separated.

---

## 33. Why do frameworks prefer RuntimeException?

**Answer:**
Cleaner APIs and better composability.

**Explanation:**
Checked exceptions do not integrate well with modern frameworks.

---

## 34. What is global exception handling?

**Answer:**
Centralized handling of exceptions at application boundaries.

**Explanation:**
Example: Spring `@ControllerAdvice`.

---

## 35. How are exceptions mapped to HTTP responses?

**Answer:**
Using exception handlers that convert exceptions into status codes.

**Explanation:**
Business exceptions → 4xx, system failures → 5xx.

---

## 36. How do exceptions behave in async code?

**Answer:**
They do not propagate automatically across threads.

**Explanation:**
They must be captured through futures or callbacks.

---

## 37. What happens to unchecked exceptions in thread pools?

**Answer:**
They terminate the task but not the JVM.

**Explanation:**
They may be lost unless explicitly retrieved.

---

## 🔴 Senior Follow-Ups

---

## 38. Why is catching Throwable bad?

**Answer:**
It hides system errors.

**Explanation:**
Critical failures like `OutOfMemoryError` may be suppressed.

---

## 39. Can finally override an exception?

**Answer:**
Yes.

**Explanation:**
An exception or return inside `finally` suppresses earlier exceptions.

---

## 40. What is the cost of throwing exceptions?

**Answer:**
Stack trace creation is expensive.

**Explanation:**
Exception creation captures execution state, making it slower than normal flow.

---

## 🧠 Universal Interview Answer

> “Exceptions define responsibility for failure. Recoverable problems are handled consciously, programming errors fail fast, and backend systems translate exceptions across layers and handle them centrally.”

---

