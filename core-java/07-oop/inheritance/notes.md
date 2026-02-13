# OOP – Lesson 3
## Inheritance (Design-Level Understanding)

Inheritance allows a class to acquire properties and behavior from another class.

But inheritance is not just reuse.
It defines a relationship: IS-A.

---

## 1. What Is Inheritance?

Inheritance means:
A subclass inherits fields and methods from a superclass.

Syntax:
class Child extends Parent

The subclass:
- Reuses code
- Can override behavior
- Can add new behavior

---

## 2. IS-A Relationship

Inheritance models IS-A relationship.

Example:
Dog IS-A Animal

If the relationship is not truly IS-A,
inheritance is incorrect.

Wrong example:
Car extends Engine ❌
Car HAS-A Engine ✅

---

## 3. Why Inheritance Exists

Inheritance provides:
- Code reuse
- Polymorphism support
- Hierarchical modeling

But code reuse alone is not a valid reason.

Correct reason:
Behavioral specialization.

---

## 4. Method Overriding

Subclass can override parent methods.

Rules:
- Same method signature
- Cannot reduce visibility
- Cannot throw broader checked exceptions
- Return type can be covariant

Runtime polymorphism is enabled through overriding.

---

## 5. super Keyword

Used to:
- Call parent constructor
- Access parent methods
- Access parent fields

Parent constructor runs before child constructor.

---

## 6. Diamond Problem

Java does not support multiple class inheritance.

Reason:
Ambiguity in method resolution.

Java solves this:
- By allowing multiple interfaces
- Using default method resolution rules

---

## 7. Problems with Inheritance

Inheritance increases:
- Tight coupling
- Fragile base class problem
- Unintended behavior changes

Changes in parent may break child classes.

Large inheritance hierarchies are hard to maintain.

---

## 8. Inheritance vs Composition

Composition:
HAS-A relationship

Preferred when:
- Behavior can change
- You want flexibility
- Avoid tight coupling

Modern backend design prefers composition.

---

## 9. Fragile Base Class Problem

If parent class changes:
- Child classes may break
- Overridden behavior may conflict

Inheritance exposes internal implementation details.

---

## 10. Backend Perspective

Inheritance is used in:
- Framework base classes
- Template methods
- Exception hierarchy

But business logic should prefer:
- Composition
- Strategy pattern
- Dependency injection

---

## 11. Common Anti-Patterns

- Inheriting just for reuse
- Deep inheritance chains
- Overriding without understanding parent contract
- Violating Liskov Substitution Principle
- Using inheritance instead of delegation

---

## 12. Interview-Safe Summary

> Inheritance models an IS-A relationship and enables runtime polymorphism, but overuse leads to tight coupling and fragile designs. Composition is often preferred in modern backend systems.
