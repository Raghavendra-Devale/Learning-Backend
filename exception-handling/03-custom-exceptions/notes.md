

# Exception Handling — Lesson 3

## Custom Exceptions, Wrapping & Best Practices

This lesson explains how to design meaningful exceptions, when to create custom exceptions, and how exception handling is structured in real backend systems.

The focus is on **expressing intent and maintaining clean system boundaries**.


## 1. Why Custom Exceptions Exist

Generic exceptions such as `Exception` or `RuntimeException`:

* Do not communicate business intent
* Make error handling ambiguous
* Reduce readability and maintainability

Custom exceptions:

* Represent domain-specific failures
* Become part of the API contract
* Allow callers to react appropriately

Examples:

* `UserNotFoundException`
* `InvalidOrderStateException`
* `PaymentFailedException`

A well-named exception explains *what went wrong* without reading implementation details.

---

## 2. Checked vs Unchecked Custom Exceptions

### Preferred Practice

Most custom exceptions should extend `RuntimeException`.

Reasons:

* Cleaner method signatures
* Easier propagation across layers
* Better compatibility with Spring and async programming
* Reduced boilerplate handling

---

### When Checked Custom Exceptions Are Appropriate

Use checked exceptions only when:

* The caller is expected to recover
* The failure is part of normal interaction with external systems
* The API must force explicit handling

Example: retryable external service failures.

---

## 3. When to Create a Custom Exception

Create custom exceptions when:

* Business rules are violated
* Domain-specific errors occur
* Additional contextual meaning is required

Avoid creating custom exceptions for:

* Programming bugs (`NullPointerException`, indexing errors)
* Purely technical failures without domain relevance

Custom exceptions should describe **business meaning**, not implementation detail.

---

## 4. Exception Wrapping

Exception wrapping means:

* Catching a low-level exception
* Throwing a higher-level exception
* Preserving the original cause

Correct pattern:

```java id="6pwz3q"
throw new BusinessException("Order processing failed", originalException);
```

### Benefits

* Preserves the original stack trace
* Retains root cause information
* Prevents leaking internal implementation details
* Adds domain context

Always pass the original exception as the cause.

---

## 5. Exception Translation Across Layers

Typical backend layering:

* **DAO layer** → throws technical exceptions
* **Service layer** → converts to business exceptions
* **Controller layer** → maps to HTTP/API responses

Each layer should:

* Translate exceptions appropriately
* Add meaningful context
* Avoid swallowing errors

Design principle:

> Translate errors, don’t expose internal details.

---

## 6. Logging Exceptions (Log Once)

Best practice:

* Log exceptions only once
* Log where the exception is finally handled

Why:

* Prevent duplicate log entries
* Reduce noise in monitoring systems
* Improve debugging clarity

Lower layers should propagate exceptions rather than log them repeatedly.

---

## 7. Avoid Using Exceptions for Control Flow

Exceptions should represent exceptional situations, not normal logic.

Bad practice:

* Using exceptions instead of condition checks

Problems:

* Exceptions are computationally expensive
* Reduce readability
* Hide expected execution paths

Use conditionals for expected outcomes.

---

## 8. Fail-Fast Principle

Fail fast when:

* Method arguments are invalid
* Object state is inconsistent
* Preconditions are violated

Common exceptions:

* `IllegalArgumentException`
* `IllegalStateException`

Failing early prevents invalid data from propagating through the system.

---

## 9. Backend Reality

In modern backend applications:

* Custom unchecked exceptions are commonly used
* Global exception handlers centralize response handling
* Business logic remains focused and clean
* Error handling is applied at system boundaries

The goal is controlled failure with clear responsibility.

---

## 10. Interview-Safe Summary

> “Custom exceptions express business intent and typically extend RuntimeException. Exceptions are wrapped to preserve causes, translated across layers, logged once at handling boundaries, and never used for normal control flow.”

---

