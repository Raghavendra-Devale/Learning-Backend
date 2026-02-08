# Exception Handling – Lesson 3  
## Custom Exceptions, Wrapping & Best Practices

This lesson focuses on designing meaningful exceptions, using custom exceptions correctly, and applying best practices used in real backend systems.

---

## 1. Why Custom Exceptions Exist

Generic exceptions like Exception or RuntimeException:
- Do not convey business meaning
- Make error handling unclear
- Reduce readability and maintainability

Custom exceptions:
- Represent domain-specific failures
- Act as part of the API contract
- Allow callers to react meaningfully

Examples:
- UserNotFoundException
- InvalidOrderStateException
- PaymentFailedException

---

## 2. Checked vs Unchecked Custom Exceptions

### Preferred Practice
Most custom exceptions should extend RuntimeException.

Reasons:
- Cleaner method signatures
- Better layering
- Easier propagation
- Works well with Spring, async code, and streams

Checked custom exceptions are used only when:
- The caller is expected to recover
- The failure is part of normal control at system boundaries

---

## 3. When to Create a Custom Exception

Create custom exceptions when:
- Business rules are violated
- Domain-specific errors occur
- Additional context is required

Do NOT create custom exceptions for:
- Programming errors (NullPointerException, IndexOutOfBoundsException)
- Low-level technical failures without business meaning

---

## 4. Exception Wrapping

Exception wrapping means:
- Catching a low-level exception
- Throwing a higher-level exception
- Preserving the original cause

Correct pattern:
```java
throw new BusinessException("Order processing failed", originalException);
````

Benefits:

* Preserves stack trace
* Retains root cause
* Prevents leaking internal implementation details

---

## 5. Exception Translation Across Layers

Typical backend layering:

* DAO layer → technical exceptions
* Service layer → business exceptions
* Controller layer → HTTP responses

Each layer:

* Translates exceptions
* Adds context
* Does not swallow errors

Design principle:

* Translate, don’t expose.

---

## 6. Logging Exceptions (Once Only)

Best practice:

* Log exceptions only once
* Log at the boundary where the exception is handled

Why:

* Avoid duplicate logs
* Reduce noise
* Improve observability

Lower layers should throw exceptions, not log them.

---

## 7. Avoid Using Exceptions for Control Flow

Exceptions should not represent normal logic.

Bad practice:

* Using exceptions instead of condition checks

Reasons:

* Exceptions are expensive
* Reduce readability
* Hide normal execution paths

Use conditionals for expected scenarios.

---

## 8. Fail-Fast Principle

Fail fast when:

* Method arguments are invalid
* Object state is illegal
* Preconditions are violated

Common exceptions:

* IllegalArgumentException
* IllegalStateException

Failing early prevents data corruption and simplifies debugging.

---

## 9. Backend Reality

In real backend systems:

* Custom RuntimeExceptions are thrown
* Global handlers manage responses
* Business logic remains clean
* Error handling is centralized

---

## 10. Interview-Safe Summary

> “Custom exceptions express business intent and usually extend RuntimeException. They are wrapped to preserve causes, translated across layers, logged once, and never used for normal control flow.”

---