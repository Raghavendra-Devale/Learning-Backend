# 🧠 Exception Handling — Twisted & Indirect Interview Questions

This file contains **indirect, scenario-based, and tricky questions**
commonly asked to test **real understanding**, not syntax.

Use this for:
- Indirect interviewers
- Design-heavy backend rounds
- Final-day revision

---

## 1️⃣ Exception Hierarchy & Root Class Traps

### Q1. Can we catch `Error`? Should we?
**Answer:**
Technically yes, but we should not.
`Error` represents JVM or system-level failures (OOM, StackOverflow)
that applications are not expected to recover from.

Safe line:
> Errors indicate serious problems that applications should not try to handle.

---

### Q2. What happens if I catch `Throwable`?
**Answer:**
It catches both `Exception` and `Error`, which is dangerous.
It can hide fatal JVM problems and lead to unstable applications.

---

### Q3. What is the root class of all exceptions?
**Answer:**
`Throwable` is the root class.
`Exception` is **not** the root.

---

## 2️⃣ Checked vs Unchecked — Indirect Questions

### Q4. Why doesn’t Java force handling `NullPointerException`?
**Answer:**
Because it represents a programming error, not a recoverable condition.
Forcing handling would hide bugs instead of fixing them.

---

### Q5. Are unchecked exceptions ignored by the JVM?
**Answer:**
No.
Unchecked exceptions are not checked at compile time,
but they still crash the program if unhandled.

---

### Q6. Why are checked exceptions controversial in modern backend systems?
**Answer:**
They are verbose, pollute method signatures, and don’t work well with
streams, lambdas, async, and layered architectures.

That’s why modern frameworks prefer unchecked exceptions.

---

## 3️⃣ try–catch–finally Killer Traps

### Q7. Does `finally` always execute?
**Answer:**
Almost always.
Exceptions include JVM crash, `System.exit()`, or power failure.

---

### Q8. What happens if `finally` has a `return` statement?
**Answer:**
The return in `finally` overrides returns from `try` or `catch`.
This is dangerous and should be avoided.

---

### Q9. What if an exception occurs inside `finally`?
**Answer:**
The exception from `finally` suppresses the original exception,
causing loss of the real root cause.

---

## 4️⃣ Exception Propagation & Wrapping

### Q10. What happens if an exception is not caught?
**Answer:**
It propagates up the call stack.
If it reaches the JVM, the program terminates.

---

### Q11. Why do we wrap exceptions?
**Answer:**
To add meaningful context and translate low-level technical exceptions
into higher-level business exceptions,
while preserving the original cause.

Golden rule:
> Never lose the root cause.

---

### Q12. What is exception swallowing and why is it bad?
**Answer:**
Catching an exception and doing nothing.
It hides failures, breaks debugging, and may leave the system inconsistent.

---

## 5️⃣ Logging Traps (Very Common)

### Q13. Should we log exceptions at every layer?
**Answer:**
No.
Exceptions should be logged once,
at the layer where they are finally handled.

---

### Q14. Where should exceptions be logged?
**Answer:**
At system boundaries (controller, message listener, entry point),
where the response or action is decided.

---

## 6️⃣ Custom Exceptions — Design Twists

### Q15. Why not throw `RuntimeException` everywhere?
**Answer:**
Generic exceptions lose meaning.
Custom exceptions make failures explicit and improve readability and handling.

---

### Q16. Should custom exceptions be checked or unchecked?
**Answer:**
Usually unchecked.
Checked custom exceptions are useful only when recovery is expected.

---

## 7️⃣ Control Flow & Anti-Patterns

### Q17. Why should exceptions not be used for control flow?
**Answer:**
They are expensive, reduce readability, and hide normal logic.
Conditions should be handled using proper checks.

---

### Q18. Why is catching generic `Exception` a bad practice?
**Answer:**
It hides specific failure types and makes handling unclear.
Always catch the most specific exception possible.

---

## 8️⃣ Backend & Concurrency Twists

### Q19. What happens to unchecked exceptions inside a thread pool?
**Answer:**
They do not crash the JVM.
They are handled by the thread and may be lost unless captured (e.g., via `Future`).

---

### Q20. Why are exceptions tricky in async or multi-threaded code?
**Answer:**
Because exceptions don’t propagate naturally across threads
and must be handled explicitly.

---

## 9️⃣ One-Line Interview Shields

Use these to stop further drilling:

- “That exception represents a programming error, not a recoverable condition.”
- “I would translate that exception at the service boundary.”
- “I would preserve the root cause while adding context.”
- “I’d let it propagate and handle it at the boundary.”

---

## ✅ Status

✔ Hierarchy traps  
✔ Checked vs unchecked twists  
✔ finally & return killers  
✔ Propagation & wrapping  
✔ Logging mistakes  
✔ Custom exception design  
✔ Async & thread pool behavior  

This file is designed to make you **exception-safe under indirect questioning**.

---
