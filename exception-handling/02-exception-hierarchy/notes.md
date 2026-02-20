

# Exception Handling — Lesson 2

## Exception Hierarchy & RuntimeException Philosophy

This lesson explains the Java exception hierarchy, the role of `RuntimeException`, and how exception design is applied in modern backend systems.

The goal is to understand **why Java separates exceptions the way it does**.

---

## 1. Root of the Exception Hierarchy

The root of all throwable objects in Java is:

```
Throwable
```

Anything that can be thrown using `throw` or propagated by the JVM must extend `Throwable`.

---

## 2. Throwable Hierarchy

`Throwable` has two direct subclasses:

* `Error`
* `Exception`

This separation distinguishes **system failures** from **application-level problems**.

```
Throwable
 ├── Error
 └── Exception
      ├── Checked Exceptions
      └── RuntimeException (Unchecked)
```

---

## 3. Error

`Error` represents:

* JVM-level failures
* Resource exhaustion
* Serious environmental problems

Examples:

* `OutOfMemoryError`
* `StackOverflowError`
* `VirtualMachineError`

**Best Practice**

* Applications should not catch or extend `Error`
* Recovery is usually unsafe because the runtime environment may already be unstable

Errors indicate the system itself is failing, not the application logic.

---

## 4. Exception

`Exception` represents problems occurring at the application level.

It is divided into:

* Checked exceptions
* Unchecked exceptions (`RuntimeException`)

This division reflects Java’s approach to handling different kinds of failures.

---

## 5. Checked Exceptions

Checked exceptions:

* Are verified at compile time
* Must be handled or declared
* Represent conditions callers may reasonably recover from

Examples:

* `IOException`
* `SQLException`
* `ClassNotFoundException`

Use checked exceptions when:

* External resources are involved (files, networks, databases)
* Failure is expected and recoverable
* API contracts must explicitly communicate risk

---

## 6. RuntimeException (Unchecked Exceptions)

`RuntimeException` represents:

* Programming mistakes
* Invalid input or arguments
* Incorrect object state
* Violated assumptions

Examples:

* `NullPointerException`
* `IllegalArgumentException`
* `IllegalStateException`
* `IndexOutOfBoundsException`

**Best Practice**

Do not catch these merely to continue execution.
They usually indicate defects that should be fixed in code.

---

## 7. Why RuntimeException Exists

Java includes `RuntimeException` because:

* Not all failures should require mandatory handling
* Some problems indicate developer errors rather than recoverable conditions
* Forced handling would encourage meaningless try–catch blocks

Design principle:

> Programmer errors should fail fast and visibly.

---

## 8. Recoverable vs Non-Recoverable Rule

A practical guideline for exception design:

* **Recoverable problems** → Checked exceptions
* **Programming errors or invalid state** → RuntimeException

This distinction helps determine whether callers should be forced to react.

---

## 9. Modern Backend Exception Design

Modern backend frameworks (Spring, Hibernate, etc.) commonly:

* Prefer unchecked exceptions
* Wrap checked exceptions into runtime exceptions
* Handle failures at application boundaries (controllers, filters, handlers)

Reason:

* Cleaner APIs
* Reduced boilerplate
* Better compatibility with functional and async programming models

---

## 10. Catching Exceptions — Best Practice

Catch exceptions only when you can:

* Recover from the problem
* Translate it into a higher-level exception
* Add meaningful context
* Log appropriately

Avoid catching exceptions simply to suppress them.

---

## 11. Exception Translation

A common backend pattern:

**Lower layers (repository / infrastructure):**

* Throw technical exceptions

**Service or boundary layers:**

* Translate exceptions into domain-specific errors
* Convert them into user-facing responses

This keeps business logic independent from low-level failures.

---

## 12. Interview-Safe Summary

> “Java’s exception hierarchy separates unrecoverable system errors from application-level exceptions, and further distinguishes recoverable checked exceptions from programming errors represented by RuntimeException.”

---

