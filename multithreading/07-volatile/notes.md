# Multithreading – Lesson 7  
## volatile Keyword (Visibility vs Atomicity)

These notes explain what the `volatile` keyword does in Java, the problem it solves, and the common interview traps associated with it.

---

## 1. The Visibility Problem

In a multithreaded environment:
- Threads may cache variables locally
- Updates made by one thread may not be visible to others immediately

This leads to visibility issues where threads operate on stale data.

---

## 2. What volatile Does

Declaring a variable as `volatile` ensures:
- Updates made by one thread are immediately visible to all other threads
- Reads always get the latest written value

This solves visibility problems.

---

## 3. What volatile Guarantees

volatile provides:
- Visibility guarantee
- Prevention of instruction reordering around the variable

It does NOT provide atomicity or mutual exclusion.

---

## 4. What volatile Does NOT Guarantee

volatile does NOT guarantee:
- Atomic operations
- Mutual exclusion
- Thread safety for compound operations

---

## 5. Why `count++` Is Not Thread-Safe with volatile

```java
volatile int count = 0;
count++;
````

The increment operation involves:

1. Read
2. Modify
3. Write

volatile ensures visibility of each step but does not make the sequence atomic.

---

## 6. volatile vs synchronized

| volatile     | synchronized                   |
| ------------ | ------------------------------ |
| Visibility   | Visibility + Mutual exclusion  |
| No locking   | Uses monitor lock              |
| Fast         | Slower than volatile           |
| No atomicity | Atomicity for critical section |

Use synchronized when multiple steps must execute together.

---

## 7. Correct Use Cases for volatile

Use volatile when:

* One thread writes
* Multiple threads read
* Operation is simple

Examples:

* Stop flags
* Status indicators
* Configuration refresh flags

---

## 8. When NOT to Use volatile

Do not use volatile when:

* Multiple threads modify the variable
* Compound operations exist
* Atomicity is required

Use synchronized or atomic classes instead.

---

## 9. Backend Reality

volatile is:

* Fast
* Limited
* Easy to misuse

Senior engineers use volatile sparingly and intentionally.

---

## 10. Interview-Safe Summary

> “volatile guarantees visibility, not atomicity. It ensures that changes to a variable are immediately visible to other threads.”

---