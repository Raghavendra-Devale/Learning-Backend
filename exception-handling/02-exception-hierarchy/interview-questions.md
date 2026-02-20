
# Interview Questions — Exception Handling (Lesson 2)


## 1. What is the root class of all exceptions in Java?

**Answer:**
`Throwable`.

**Explanation:**
Only objects extending `Throwable` can be thrown using the `throw` keyword. Both system errors and application exceptions originate from this class.

---

## 2. What are the two direct subclasses of Throwable?

**Answer:**
`Error` and `Exception`.

**Explanation:**
Java separates failures into system-level problems (`Error`) and application-level problems (`Exception`) to distinguish recoverability.

---

## 3. Difference between Error and Exception?

**Answer:**
`Error` represents unrecoverable JVM-level problems, while `Exception` represents application-level issues.

**Explanation:**
Errors usually indicate environment failure (memory exhaustion, JVM issues), whereas exceptions are conditions applications are expected to handle or propagate.

---

## 4. What is RuntimeException?

**Answer:**
`RuntimeException` represents unchecked exceptions that typically indicate programming errors.

**Explanation:**
These exceptions occur due to invalid assumptions in code, such as null access or illegal arguments, and are not enforced by the compiler.

---

## 5. Why does RuntimeException exist?

**Answer:**
To represent failures that should not require mandatory handling.

**Explanation:**
Forcing developers to handle programming bugs would encourage unnecessary try–catch blocks and hide defects instead of fixing them.

---

## 6. Difference between checked and unchecked exceptions?

**Answer:**
Checked exceptions are enforced at compile time and represent recoverable conditions, while unchecked exceptions represent programming errors.

**Explanation:**
Checked exceptions force callers to acknowledge possible failure, whereas unchecked exceptions signal problems that should be corrected in the code itself.

---

## 7. When should checked exceptions be used?

**Answer:**
When the caller can reasonably recover from the failure.

**Explanation:**
They are appropriate at boundaries involving external systems such as file operations, network communication, or database access.

---

## 8. When should RuntimeException be thrown?

**Answer:**
When method preconditions are violated or object state becomes invalid.

**Explanation:**
Examples include passing illegal arguments or calling methods at the wrong lifecycle stage. These indicate misuse of an API rather than environmental failure.

---

## 9. Is IndexOutOfBoundsException recoverable?

**Answer:**
No.

**Explanation:**
It indicates incorrect logic in indexing operations and should be fixed in the code instead of handled at runtime.

---

## 10. Why do modern frameworks prefer RuntimeException?

**Answer:**
To avoid cluttered method signatures and enable cleaner APIs.

**Explanation:**
Unchecked exceptions work better with dependency injection, streams, and asynchronous programming, reducing boilerplate error handling.

---

## 11. Where should exceptions ideally be caught?

**Answer:**
At application boundaries where meaningful handling or translation can occur.

**Explanation:**
Lower layers usually propagate exceptions, while higher layers convert them into domain errors, logs, or API responses.

---

## 12. What is exception translation?

**Answer:**
Converting low-level exceptions into higher-level, meaningful exceptions.

**Explanation:**
For example, converting `SQLException` into a business exception like `OrderProcessingException` to hide implementation details.

---

## 13. Should RuntimeException be caught?

**Answer:**
Generally no, unless adding context or translating the exception.

**Explanation:**
Catching runtime exceptions purely to continue execution may hide programming errors.

---

## 14. What happens if a RuntimeException is not caught?

**Answer:**
It propagates up the call stack and may terminate the application.

**Explanation:**
If no handler exists, the JVM stops execution of the current thread and prints the stack trace.

---

## 15. Why is catching Exception considered bad practice?

**Answer:**
Because it hides specific failure types.

**Explanation:**
Catching broad exceptions makes debugging harder and may unintentionally handle errors that should propagate further.

---

## Common Interview Traps & Pitfalls

❌ Saying `Exception` is the root class
❌ Treating `RuntimeException` as recoverable by default
❌ Catching `Exception` everywhere
❌ Using checked exceptions for programming bugs
❌ Over-handling instead of propagating

---

## One Interview-Safe Explanation

> “Throwable is the root of Java’s exception hierarchy. Checked exceptions represent recoverable failures, while RuntimeException represents programming errors that should generally be fixed rather than handled.”

---

Here’s the deeper pattern interviewers quietly evaluate: whether you understand that exceptions are about **responsibility boundaries** — deciding *who* should handle failure and *where* it should be understood. Once that clicks, exception questions stop feeling theoretical and start feeling architectural.
