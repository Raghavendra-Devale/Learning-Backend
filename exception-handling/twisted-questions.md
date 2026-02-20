

# 🧠 Exception Handling — Twisted & Indirect Interview Questions

This section contains **indirect, scenario-based, and tricky questions** commonly used to test **real understanding**, not syntax memorization.

Use this for:

* Indirect or probing interviewers
* Design-heavy backend rounds
* Final-day revision before interviews



## 1️⃣ Exception Hierarchy & Root Class Traps

### Q1. Can we catch `Error`? Should we?

**Answer:**
Technically yes, but it should generally not be done.

`Error` represents JVM or system-level failures (e.g., `OutOfMemoryError`, `StackOverflowError`) from which applications are not expected to recover safely.

Safe explanation:

> Errors indicate serious system problems that application code should not attempt to handle.

---

### Q2. What happens if I catch `Throwable`?

**Answer:**
It catches both `Exception` and `Error`, which is dangerous.

Catching `Throwable` may hide fatal JVM failures and leave the application in an unstable state. Always catch specific exceptions instead.

---

### Q3. What is the root class of all exceptions?

**Answer:**
`Throwable`.

**Explanation:**
Both `Error` and `Exception` extend `Throwable`.
`Exception` is **not** the root of the hierarchy.

---

## 2️⃣ Checked vs Unchecked — Indirect Questions

### Q4. Why doesn’t Java force handling `NullPointerException`?

**Answer:**
Because it represents a programming error rather than a recoverable condition.

Forcing handling would encourage hiding bugs instead of fixing incorrect logic.

---

### Q5. Are unchecked exceptions ignored by the JVM?

**Answer:**
No.

Unchecked exceptions are only unchecked at **compile time**.
If unhandled, they still propagate and terminate the executing thread.

---

### Q6. Why are checked exceptions controversial in modern backend systems?

**Answer:**
They are verbose, pollute method signatures, and integrate poorly with streams, lambdas, async workflows, and layered architectures.

Modern frameworks often convert checked exceptions into runtime exceptions to simplify APIs.

---

## 3️⃣ try–catch–finally Killer Traps

### Q7. Does `finally` always execute?

**Answer:**
Almost always.

Exceptions include:

* JVM crash
* `System.exit()`
* abrupt process termination or power failure

---

### Q8. What happens if `finally` has a `return` statement?

**Answer:**
The return in `finally` overrides returns from `try` or `catch`.

This can suppress exceptions or change return values and is considered a dangerous anti-pattern.

---

### Q9. What if an exception occurs inside `finally`?

**Answer:**
The exception thrown in `finally` suppresses the original exception, potentially hiding the real root cause.

---

## 4️⃣ Exception Propagation & Wrapping

### Q10. What happens if an exception is not caught?

**Answer:**
It propagates up the call stack.

If no handler is found, the JVM terminates the executing thread and prints the stack trace.

---

### Q11. Why do we wrap exceptions?

**Answer:**
To add business context while preserving the original technical cause.

Wrapping allows translation of low-level exceptions into meaningful domain exceptions without losing debugging information.

Golden rule:

> Never lose the root cause.

---

### Q12. What is exception swallowing and why is it bad?

**Answer:**
Catching an exception and doing nothing with it.

Problems caused:

* Hidden failures
* Broken observability
* Difficult debugging
* Potentially inconsistent system state

---

## 5️⃣ Logging Traps (Very Common)

### Q13. Should we log exceptions at every layer?

**Answer:**
No.

Exceptions should be logged once — where they are finally handled.

Multiple logs create duplicated stack traces and monitoring noise.

---

### Q14. Where should exceptions be logged?

**Answer:**
At application boundaries, such as:

* Controllers
* Global exception handlers
* Message listeners
* Entry-point layers

This is where the final response or corrective action is decided.

---

## 6️⃣ Custom Exceptions — Design Twists

### Q15. Why not throw `RuntimeException` everywhere?

**Answer:**
Generic exceptions lose semantic meaning.

Custom exceptions clearly express business intent and make handling and debugging easier.

---

### Q16. Should custom exceptions be checked or unchecked?

**Answer:**
Usually unchecked.

Checked custom exceptions are appropriate only when callers are expected to recover from the failure.

---

## 7️⃣ Control Flow & Anti-Patterns

### Q17. Why should exceptions not be used for control flow?

**Answer:**
Because exceptions:

* are computationally expensive
* reduce readability
* obscure normal execution paths

Exceptions should represent unexpected situations only.

---

### Q18. Why is catching generic `Exception` bad practice?

**Answer:**
It hides specific failure types and makes correct handling unclear.

Always catch the most specific exception possible.

---

## 8️⃣ Backend & Concurrency Twists

### Q19. What happens to unchecked exceptions inside a thread pool?

**Answer:**
They terminate the executing task but do not crash the JVM.

If not explicitly retrieved (e.g., via `Future.get()`), the exception may appear lost.

---

### Q20. Why are exceptions tricky in async or multi-threaded code?

**Answer:**
Because exceptions do not automatically propagate across threads.

They must be captured and handled explicitly using futures, callbacks, or completion stages.

---

## 9️⃣ One-Line Interview Shields

Use concise reasoning statements when interviewers probe deeply:

* “That represents a programming error, not a recoverable condition.”
* “I would translate this exception at the service boundary.”
* “I would preserve the root cause while adding context.”
* “I’d let it propagate and handle it at the boundary.”

These demonstrate architectural thinking and usually conclude deep probing.

---


