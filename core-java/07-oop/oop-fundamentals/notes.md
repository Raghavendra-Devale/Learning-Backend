# OOP – Lesson 1
## Fundamentals & Design Philosophy

This lesson explains what Object-Oriented Programming (OOP) truly solves, beyond textbook definitions.

---

## 1. Why OOP Exists

OOP exists to manage complexity in large systems.

Procedural programming separates data and behavior, which:
- Makes systems harder to scale
- Allows uncontrolled state mutation
- Increases coupling

OOP binds data and behavior together to:
- Protect invariants
- Improve modularity
- Control state transitions
- Reduce accidental misuse

Core idea:
An object owns its state and controls how it changes.

---

## 2. What Is an Object?

An object has:
- State (fields)
- Behavior (methods)
- Identity (memory reference)

More importantly:
- It encapsulates its state
- It exposes controlled behavior

Example:
A `User` object should manage its own password changes, status updates, and role assignments.

---

## 3. What Is a Class?

A class is:
- A blueprint or template
- Defines structure and behavior

An object is:
- A runtime instance of a class
- Allocated in heap memory
- Has identity

Interview depth:
Classes themselves are objects of type `Class` in Java.

---

## 4. OOP vs Procedural Programming

Procedural:
- Functions operate on data
- State often exposed
- Global state risk

OOP:
- State and behavior combined
- Objects manage responsibilities
- Better encapsulation

OOP supports layered backend architecture:
- Controller
- Service
- Repository
- Entity

---

## 5. The Real Pillars (Clarified)

Traditional pillars:
- Encapsulation
- Abstraction
- Inheritance
- Polymorphism

In modern backend design:
- Encapsulation and Polymorphism are most critical
- Inheritance is often overused
- Abstraction defines boundaries

---

## 6. Design Benefits of OOP

- Modularity
- Reusability
- Maintainability
- Extensibility
- Clear responsibility separation

---

## 7. Common Misuse of OOP

- Overusing inheritance
- Breaking encapsulation
- Creating god objects
- Tight coupling
- Over-abstracting early

OOP is powerful only when responsibilities are well-designed.

---

## 8. Backend Perspective

OOP enables:
- Layered architecture
- Dependency injection
- Domain modeling
- Clean API contracts

Well-designed objects protect business invariants and simplify reasoning.

---

## 9. Interview-Safe Summary

> OOP manages system complexity by binding state and behavior together, enabling modular, maintainable, and scalable backend systems.
