# OOP – Lesson 5
## Abstraction (Design-Level Understanding)

Abstraction means hiding implementation details and exposing only essential behavior.

Core idea:
Show WHAT to do, hide HOW it is done.

---

## 1. What Is Abstraction?

Abstraction reduces complexity by:
- Exposing only required operations
- Hiding internal logic
- Defining contracts

Example:
List interface hides internal implementation (ArrayList, LinkedList).

---

## 2. Abstraction vs Encapsulation

Encapsulation:
Protects internal state.

Abstraction:
Hides implementation complexity.

Encapsulation = protecting data  
Abstraction = hiding complexity

They work together but are different concepts.

---

## 3. Ways to Achieve Abstraction in Java

1. Interfaces
2. Abstract classes

---

## 4. Interface

Interface:
- Defines a contract
- Contains abstract methods (Java 8+ can have default & static methods)
- Supports multiple inheritance

Used when:
- Behavior is independent of implementation
- Loose coupling is required
- Strategy pattern is needed

Example:
PaymentService

---

## 5. Abstract Class

Abstract class:
- Can have abstract and concrete methods
- Can have constructors
- Can have state
- Supports single inheritance

Used when:
- Some shared implementation exists
- Hierarchy makes sense
- Partial behavior is common

Example:
AbstractPaymentProcessor

---

## 6. Interface vs Abstract Class (Key Differences)

Interface:
- Pure contract
- Multiple inheritance allowed
- No instance state (except constants)
- Promotes loose coupling

Abstract class:
- Partial implementation
- Single inheritance
- Can maintain common state
- Stronger coupling

---

## 7. Modern Backend Preference

Modern backend systems prefer:
Interfaces + composition

Why?
- Better flexibility
- Easier testing
- Supports dependency injection
- Avoids fragile hierarchies

---

## 8. Abstraction and Dependency Injection

Spring uses abstraction heavily:
- Controller depends on interface
- Implementation injected at runtime

Example:
NotificationService → EmailNotificationService / SMSNotificationService

This enables:
- Loose coupling
- Runtime swapping
- Open-Closed Principle

---

## 9. Common Mistakes

- Creating interface for every class blindly
- Using abstract class when interface is better
- Tight coupling through abstract base classes
- Misunderstanding default methods

---

## 10. Interview-Safe Summary

> Abstraction hides implementation details and exposes only required behavior, typically achieved using interfaces or abstract classes, enabling loose coupling and flexible backend design.
