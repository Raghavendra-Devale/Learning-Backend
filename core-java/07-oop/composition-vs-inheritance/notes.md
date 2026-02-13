# OOP – Lesson 7
## Composition vs Inheritance (Design-Level Understanding)

Inheritance defines an IS-A relationship.
Composition defines a HAS-A relationship.

Modern backend systems prefer composition over inheritance.

---

## 1. What Is Composition?

Composition means:
An object contains another object as a field.

Example:
class Car {
private Engine engine;
}

Car HAS-A Engine.

---

## 2. Inheritance vs Composition

Inheritance:
- IS-A relationship
- Tight coupling
- Behavior inherited
- Parent changes affect child

Composition:
- HAS-A relationship
- Loose coupling
- Behavior delegated
- More flexible

---

## 3. Why Composition Is Preferred

Inheritance problems:
- Fragile base class problem
- Tight coupling
- Deep hierarchies become hard to maintain
- Hard to modify behavior dynamically

Composition advantages:
- Change behavior at runtime
- Replace components easily
- Better testing
- Supports dependency injection

---

## 4. Fragile Base Class Problem

If parent changes:
- Child behavior may break
- Unexpected bugs appear
- Overridden methods conflict

Composition avoids this.

---

## 5. Strategy Pattern Example

Instead of:

class Bird extends FlyingBird

Use:

class Bird {
private FlyBehavior flyBehavior;
}

Behavior is injected.

This enables:
- Runtime flexibility
- Open-Closed Principle
- Easier maintenance

---

## 6. Real Backend Example

Bad inheritance:
class MyService extends BaseService

Better composition:
class MyService {
private Validator validator;
private Repository repository;
}

Dependencies injected.

---

## 7. When to Use Inheritance

Use inheritance when:
- True IS-A relationship
- Stable hierarchy
- Shared contract required
- Framework base class extension

Use composition when:
- Behavior may vary
- Runtime flexibility required
- You want loose coupling
- Testing is important

---

## 8. Composition and Dependency Injection

Spring relies heavily on composition.

Beans:
- Injected as dependencies
- Not inherited

Loose coupling is core design goal.

---

## 9. Common Anti-Patterns

- Inheriting just for reuse
- Deep inheritance chains
- Using inheritance instead of delegation
- Violating Liskov Substitution Principle

---

## 10. Interview-Safe Summary

> Inheritance models IS-A relationships but introduces tight coupling, while composition models HAS-A relationships and provides flexibility, loose coupling, and better maintainability in backend systems.
s