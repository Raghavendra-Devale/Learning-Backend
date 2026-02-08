# Interview Questions – Exception Handling (Lesson 1)

---

## 1. What is an exception?
An exception represents an abnormal condition that disrupts normal program flow and requires handling.

---

## 2. Difference between Error and Exception?
Error represents serious JVM-level problems that applications should not recover from, while Exception represents application-level issues that can be handled.

---

## 3. Should we catch Errors?
No. Errors indicate unrecoverable conditions and should not be handled by application code.

---

## 4. What are checked exceptions?
Checked exceptions are exceptions that the compiler forces the developer to handle or declare at compile time.

---

## 5. What are unchecked exceptions?
Unchecked exceptions are runtime exceptions that are not checked at compile time and usually represent programming bugs.

---

## 6. Give examples of checked exceptions.
IOException, SQLException.

---

## 7. Give examples of unchecked exceptions.
NullPointerException, IndexOutOfBoundsException, IllegalArgumentException.

---

## 8. Why does Java have checked exceptions?
To force developers to explicitly handle recoverable failure scenarios and avoid silent failures.

---

## 9. Why are checked exceptions controversial?
They increase verbosity, pollute method signatures, and are difficult to use with modern async and functional programming.

---

## 10. Should unchecked exceptions be caught?
Usually no. They indicate bugs and should be fixed rather than handled.

---

## 11. What is exception propagation?
If an exception is not handled in a method, it propagates up the call stack until handled or the JVM terminates the program.

---

## 12. What is the purpose of finally block?
To perform cleanup actions that must execute regardless of whether an exception occurs.

---

## 13. Does finally always execute?
Yes, except in cases like JVM crash or System.exit().

---

## 14. What is exception swallowing?
Catching an exception without handling or logging it.

---

## 15. Why is swallowing exceptions dangerous?
It hides failures, makes debugging difficult, and can leave the system in an inconsistent state.

---

## 16. How are exceptions handled in real backend applications?
They are logged, translated, and mapped to meaningful responses rather than swallowed.

---

## Common Interview Traps & Pitfalls

❌ Saying checked exceptions occur at runtime  
❌ Catching RuntimeException everywhere  
❌ Swallowing exceptions  
❌ Catching Exception instead of specific exceptions  
❌ Assuming finally always runs in every scenario  

---

## One Interview-Safe Explanation

> “Checked exceptions enforce handling of recoverable failures at compile time, while unchecked exceptions represent programming errors and should usually be fixed, not caught.”

---