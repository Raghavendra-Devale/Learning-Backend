# Interview Questions – Exception Handling (Lesson 2)

---

## 1. What is the root class of all exceptions in Java?
Throwable.

---

## 2. What are the two direct subclasses of Throwable?
Error and Exception.

---

## 3. Difference between Error and Exception?
Error represents unrecoverable JVM-level problems, while Exception represents application-level issues.

---

## 4. What is RuntimeException?
RuntimeException represents unchecked exceptions that indicate programming errors or bugs.

---

## 5. Why does RuntimeException exist?
To represent bugs that should not be forced to be handled and should instead be fixed.

---

## 6. Difference between checked and unchecked exceptions?
Checked exceptions are enforced at compile time and represent recoverable conditions, while unchecked exceptions represent programming errors.

---

## 7. When should checked exceptions be used?
When the caller can reasonably recover, especially at system or IO boundaries.

---

## 8. When should RuntimeException be thrown?
When method preconditions are violated or object state is invalid.

---

## 9. Is IndexOutOfBoundsException recoverable?
No. It indicates a programming bug and should be fixed.

---

## 10. Why do modern frameworks prefer RuntimeException?
To avoid polluting method signatures and to support clean, composable APIs.

---

## 11. Where should exceptions ideally be caught?
At boundaries where meaningful handling, translation, or logging can be done.

---

## 12. What is exception translation?
Converting low-level exceptions into higher-level, meaningful exceptions.

---

## 13. Should RuntimeException be caught?
Generally no, unless translating or adding context.

---

## 14. What happens if a RuntimeException is not caught?
It propagates up the call stack and may terminate the application.

---

## 15. Why is catching Exception considered bad practice?
It hides specific failures and makes debugging difficult.

---

## Common Interview Traps & Pitfalls

❌ Saying Exception is the root class  
❌ Treating RuntimeException as recoverable  
❌ Catching Exception everywhere  
❌ Using checked exceptions for programming bugs  
❌ Over-handling exceptions  

---

## One Interview-Safe Explanation

> “Throwable is the root of Java’s exception hierarchy. Checked exceptions represent recoverable failures, while RuntimeException represents programming errors and should usually not be handled but fixed.”

---
