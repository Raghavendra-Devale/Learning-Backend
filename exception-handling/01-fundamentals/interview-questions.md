

# Interview Questions — Exception Handling (Lesson 1)


## 1. What is an exception?

**Answer:**
An exception represents an abnormal condition that disrupts normal program flow and requires handling.

**Explanation:**
Instead of crashing silently, Java throws an exception object to signal failure, allowing the program to handle or propagate the problem in a controlled way.

---

## 2. Difference between Error and Exception?

**Answer:**
`Error` represents serious JVM-level problems, while `Exception` represents application-level issues that can be handled.

**Explanation:**
Errors usually indicate system failures such as memory exhaustion, whereas exceptions represent conditions applications are expected to manage or recover from.

---

## 3. Should we catch Errors?

**Answer:**
No, Errors should generally not be caught.

**Explanation:**
Errors indicate unrecoverable situations where the JVM or application state may already be unstable, making recovery unsafe.

---

## 4. What are checked exceptions?

**Answer:**
Checked exceptions are exceptions that the compiler forces the developer to handle or declare.

**Explanation:**
The compiler ensures that potentially recoverable failures are explicitly acknowledged using `try–catch` or `throws`.

---

## 5. What are unchecked exceptions?

**Answer:**
Unchecked exceptions are runtime exceptions not verified at compile time and usually indicate programming mistakes.

**Explanation:**
They arise from invalid assumptions in code, such as accessing null references or invalid indexes.

---

## 6. Give examples of checked exceptions.

**Answer:**
`IOException`, `SQLException`, `ClassNotFoundException`.

**Explanation:**
These represent external or environmental failures that applications may reasonably recover from.

---

## 7. Give examples of unchecked exceptions.

**Answer:**
`NullPointerException`, `IndexOutOfBoundsException`, `IllegalArgumentException`.

**Explanation:**
These typically result from coding errors rather than external conditions.

---

## 8. Why does Java have checked exceptions?

**Answer:**
To force developers to explicitly handle recoverable failure scenarios.

**Explanation:**
Checked exceptions make failure visible in method signatures, ensuring callers consciously decide how to handle errors.

---

## 9. Why are checked exceptions controversial?

**Answer:**
They increase verbosity and complicate modern programming patterns.

**Explanation:**
They add boilerplate code and do not integrate smoothly with streams, lambdas, and asynchronous APIs, leading many frameworks to wrap them into runtime exceptions.

---

## 10. Should unchecked exceptions be caught?

**Answer:**
Usually no.

**Explanation:**
Unchecked exceptions typically indicate bugs. Fixing the root cause is preferred over catching and hiding the problem.

---

## 11. What is exception propagation?

**Answer:**
When an exception is not handled in a method, it moves up the call stack until handled or the program terminates.

**Explanation:**
Each calling method gets an opportunity to handle the exception, enabling centralized error handling.

---

## 12. What is the purpose of the `finally` block?

**Answer:**
To execute cleanup logic regardless of whether an exception occurs.

**Explanation:**
It ensures resources such as files, sockets, or database connections are released properly.

---

## 13. Does `finally` always execute?

**Answer:**
Almost always, except during JVM termination or `System.exit()`.

**Explanation:**
If the JVM stops execution abruptly, the `finally` block may not run.

---

## 14. What is exception swallowing?

**Answer:**
Catching an exception without handling or logging it.

**Explanation:**
This hides failures and removes visibility into system problems.

---

## 15. Why is swallowing exceptions dangerous?

**Answer:**
It hides bugs and may leave the system in an inconsistent state.

**Explanation:**
Without logs or handling, failures become difficult to diagnose and may cause unpredictable behavior later.

---

## 16. How are exceptions handled in real backend applications?

**Answer:**
Exceptions are logged, translated, and mapped into meaningful responses.

**Explanation:**
Low-level exceptions are usually converted into domain-specific or API-level errors rather than exposed directly.

---

## Common Interview Traps & Pitfalls

❌ Saying checked exceptions occur only at runtime
❌ Catching `RuntimeException` everywhere
❌ Swallowing exceptions silently
❌ Catching generic `Exception` instead of specific types
❌ Assuming `finally` executes in every possible scenario

---

## One Interview-Safe Explanation

> “Checked exceptions enforce handling of recoverable failures at compile time, while unchecked exceptions typically represent programming errors that should be fixed rather than caught.”

---

