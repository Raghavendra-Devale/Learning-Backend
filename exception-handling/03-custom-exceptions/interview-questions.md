# Interview Questions – Exception Handling (Lesson 3)

---

## 1. Why do we need custom exceptions?
To represent domain-specific failures clearly and make error handling meaningful.

---

## 2. Should custom exceptions be checked or unchecked?
Usually unchecked (RuntimeException), unless recovery is expected.

---

## 3. Why are unchecked exceptions preferred in backend systems?
They avoid cluttered method signatures and work better with layered, async, and framework-based designs.

---

## 4. What is exception wrapping?
Catching a low-level exception and rethrowing a higher-level exception while preserving the original cause.

---

## 5. Why is exception wrapping important?
It preserves stack traces, keeps root cause information, and hides implementation details.

---

## 6. What is exception translation?
Converting low-level technical exceptions into meaningful business or domain exceptions.

---

## 7. Where should exceptions be logged?
At the boundary where they are handled and translated, usually once.

---

## 8. Why should exceptions be logged only once?
To avoid duplicate logs, noise, and confusion during debugging.

---

## 9. Why should exceptions not be used for control flow?
They are expensive, reduce readability, and hide normal execution paths.

---

## 10. What does “fail fast” mean?
Throwing exceptions early when invalid input or state is detected.

---

## 11. Give examples of fail-fast exceptions.
IllegalArgumentException, IllegalStateException.

---

## 12. Should lower layers log exceptions?
No. Lower layers should throw exceptions; upper layers handle and log them.

---

## 13. When should you NOT create a custom exception?
For programming bugs or generic technical failures without business meaning.

---

## Common Interview Traps & Pitfalls

❌ Creating too many custom exceptions  
❌ Extending Exception unnecessarily  
❌ Losing original exception cause  
❌ Logging exceptions in every layer  
❌ Using exceptions as normal control flow  

---

## One Interview-Safe Explanation

> “Custom exceptions communicate business intent. They usually extend RuntimeException, preserve causes through wrapping, are translated across layers, and are logged once at system boundaries.”

---