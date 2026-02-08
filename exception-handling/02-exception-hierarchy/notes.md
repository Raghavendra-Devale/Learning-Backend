# Exception Handling – Lesson 2  
## Exception Hierarchy & RuntimeException Philosophy

This lesson explains the Java exception hierarchy, the purpose of RuntimeException, and how exception design is handled in real backend systems.

---

## 1. Root of Exception Hierarchy

The root class of all exceptions and errors in Java is:

Throwable

Everything that can be thrown in Java extends Throwable.

---

## 2. Throwable Hierarchy

Throwable has two direct subclasses:
- Error
- Exception

This separation is intentional and fundamental to Java’s design.

---

## 3. Error

Error represents:
- JVM-level or system-level problems
- Resource exhaustion or environment failures

Examples:
- OutOfMemoryError
- StackOverflowError

Best practice:
- Applications should not catch or extend Error
- Errors indicate the environment is broken

---

## 4. Exception

Exception represents application-level problems.

It is divided into:
- Checked exceptions
- Unchecked exceptions (RuntimeException)

This division defines Java’s error-handling philosophy.

---

## 5. Checked Exceptions

Checked exceptions:
- Are checked at compile time
- Must be handled or declared
- Represent recoverable conditions

Examples:
- IOException
- SQLException

Use checked exceptions when:
- Caller can reasonably recover
- External systems are involved
- API boundaries exist

---

## 6. RuntimeException (Unchecked Exceptions)

RuntimeException represents:
- Programming mistakes
- Invalid arguments
- Illegal object state
- Broken assumptions

Examples:
- NullPointerException
- IllegalArgumentException
- IllegalStateException
- IndexOutOfBoundsException

Best practice:
- Do not catch to recover
- Fix the code instead

---

## 7. Why RuntimeException Exists

RuntimeException exists because:
- Not all failures should be forced to be handled
- Some problems indicate bugs, not recoverable conditions
- Forcing handling would hide bugs

Design principle:
- Fail fast on programmer errors

---

## 8. Recoverable vs Non-Recoverable Rule

- Recoverable problems → Checked exceptions
- Programming bugs → RuntimeException

This rule guides exception design.

---

## 9. Modern Backend Exception Design

Modern frameworks (Spring, Hibernate):
- Prefer RuntimeException
- Wrap checked exceptions
- Handle errors at system boundaries

This avoids polluting method signatures.

---

## 10. Catching Exceptions — Best Practice

Catch exceptions only when you can:
- Recover
- Translate
- Add context
- Log meaningfully

Avoid catching exceptions just to suppress them.

---

## 11. Exception Translation

Lower layers:
- Throw RuntimeException

Upper layers:
- Translate exceptions
- Map them to user-friendly responses

This keeps business logic clean.

---

## 12. Interview-Safe Summary

> “Java’s exception hierarchy separates unrecoverable system errors from application-level exceptions, and further distinguishes recoverable checked exceptions from programming errors represented by RuntimeException.”

---
