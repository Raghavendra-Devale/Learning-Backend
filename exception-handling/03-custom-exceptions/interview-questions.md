
# Interview Questions — Exception Handling (Lesson 3)


## 1. Why do we need custom exceptions?

**Answer:**
To represent domain-specific failures clearly and make error handling meaningful.

**Explanation:**
Generic exceptions do not convey business intent. A custom exception communicates what actually failed (for example, `UserNotFoundException`), making code easier to understand and handle correctly.

---

## 2. Should custom exceptions be checked or unchecked?

**Answer:**
Usually unchecked (`RuntimeException`), unless recovery is expected.

**Explanation:**
Unchecked exceptions propagate naturally across layers without forcing boilerplate handling. Checked exceptions are used only when callers must actively recover from the failure.

---

## 3. Why are unchecked exceptions preferred in backend systems?

**Answer:**
They avoid cluttered method signatures and integrate better with layered and framework-based designs.

**Explanation:**
Modern frameworks, async processing, and functional APIs work more cleanly with unchecked exceptions, reducing unnecessary try–catch blocks.

---

## 4. What is exception wrapping?

**Answer:**
Catching a low-level exception and rethrowing a higher-level exception while preserving the original cause.

**Explanation:**
Wrapping adds business context while keeping the original stack trace available for debugging.

---

## 5. Why is exception wrapping important?

**Answer:**
It preserves stack traces, retains root cause information, and hides internal implementation details.

**Explanation:**
Users and higher layers see meaningful errors, while developers can still trace the underlying technical failure.

---

## 6. What is exception translation?

**Answer:**
Converting low-level technical exceptions into meaningful business or domain exceptions.

**Explanation:**
For example, converting a `SQLException` into `OrderProcessingException` prevents leaking database details into business logic or APIs.

---

## 7. Where should exceptions be logged?

**Answer:**
At the boundary where they are handled and translated.

**Explanation:**
This is typically the controller or global handler layer, where the system decides the final response.

---

## 8. Why should exceptions be logged only once?

**Answer:**
To avoid duplicate logs and debugging confusion.

**Explanation:**
Logging in multiple layers creates repeated stack traces, making monitoring noisy and harder to analyze.

---

## 9. Why should exceptions not be used for control flow?

**Answer:**
Because they are expensive and obscure normal execution logic.

**Explanation:**
Exceptions are designed for unexpected situations. Using them for expected outcomes reduces readability and harms performance.

---

## 10. What does “fail fast” mean?

**Answer:**
Throwing exceptions immediately when invalid input or state is detected.

**Explanation:**
Failing early prevents corrupted data or invalid state from spreading deeper into the system.

---

## 11. Give examples of fail-fast exceptions.

**Answer:**
`IllegalArgumentException`, `IllegalStateException`.

**Explanation:**
These exceptions signal incorrect usage of methods or invalid object state at the moment the problem occurs.

---

## 12. Should lower layers log exceptions?

**Answer:**
No. Lower layers should throw exceptions; upper layers handle and log them.

**Explanation:**
Centralized logging avoids duplication and keeps infrastructure code clean.

---

## 13. When should you NOT create a custom exception?

**Answer:**
For programming bugs or generic technical failures without business meaning.

**Explanation:**
Custom exceptions should express domain intent, not replace existing standard exceptions unnecessarily.

---

## Common Interview Traps & Pitfalls

❌ Creating excessive custom exceptions without clear purpose
❌ Extending `Exception` when unchecked exceptions are sufficient
❌ Losing the original exception cause during wrapping
❌ Logging exceptions in every layer
❌ Using exceptions for normal program logic

---

## One Interview-Safe Explanation

> “Custom exceptions communicate business intent. They typically extend RuntimeException, preserve causes through wrapping, are translated across layers, and are logged once at system boundaries.”

---

