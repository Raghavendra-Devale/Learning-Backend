

# OOP – Lesson 2  
## Encapsulation (Design-Level Understanding)

## 1. What Is Encapsulation?

Encapsulation is the practice of:
- Bundling state (fields) and behavior (methods)
- Restricting direct access to internal state
- Exposing controlled operations

Core idea:
Objects should control how their internal state changes.

---

## 2. Why Encapsulation Exists

Without encapsulation:
- Any code can mutate object state
- Invariants can be broken
- Debugging becomes difficult
- Concurrency bugs increase

Encapsulation ensures:
- Valid state
- Controlled transitions
- Predictable behavior

---

## 3. Encapsulation vs Data Hiding

Data hiding:
- Restricting access using private modifiers

Encapsulation:
- Designing methods that enforce rules
- Protecting invariants
- Controlling object behavior

Data hiding is a tool.
Encapsulation is a design principle.

---

## 4. Protecting Invariants

Invariant:
A rule that must always remain true.

Example:
A bank account balance must never be negative.

Bad:
```java
account.balance = -100;
````

Good:

```java
account.withdraw(100);
```

The object validates and enforces rules internally.

---

## 5. Encapsulation and Concurrency

Broken encapsulation increases race conditions.

If fields are public:

* Multiple threads may modify state directly
* No validation or synchronization control

Encapsulation allows:

* Synchronization inside methods
* Controlled atomic operations

This reduces concurrency bugs.

---

## 6. Getter and Setter Myth

Encapsulation is NOT:

* Automatically generating getters and setters

Bad practice:
Exposing setters for all fields without validation.

Good practice:

* Provide only meaningful operations
* Avoid unnecessary setters
* Keep object state consistent

---

## 7. Immutable Objects Strengthen Encapsulation

Immutable objects:

* Do not allow state changes after creation
* Eliminate synchronization needs
* Prevent invariant violations

Example:
String class in Java.

---

## 8. Backend Perspective

Encapsulation:

* Protects domain models
* Prevents invalid business states
* Supports clean service layers
* Reduces debugging complexity

In DDD (Domain-Driven Design):
Entities must guard their own invariants.

---

## 9. Common Anti-Patterns

* Public fields
* Exposing internal collections directly
* Excessive setters
* Returning mutable internal references
* God objects with too much responsibility

---

## 10. Interview-Safe Summary

> Encapsulation protects object invariants by restricting direct state access and exposing controlled behavior, ensuring consistency, maintainability, and safer concurrent design.