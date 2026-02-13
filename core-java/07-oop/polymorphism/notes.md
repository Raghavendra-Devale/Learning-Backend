# OOP – Lesson 4
## Polymorphism

Polymorphism means "many forms".

In OOP, it allows objects to behave differently through a common interface or superclass.

Core idea:
One interface, multiple implementations.

---

## 1. Types of Polymorphism in Java

1. Compile-time polymorphism (Static binding)
2. Runtime polymorphism (Dynamic binding)

---

## 2. Compile-Time Polymorphism (Method Overloading)

Same method name, different parameters.

Example:
add(int a, int b)
add(double a, double b)

Resolution:
Happens at compile time.

Key points:
- Based on method signature
- Not true behavioral polymorphism
- Decided by reference type at compile time

---

## 3. Runtime Polymorphism (Method Overriding)

Child class overrides parent method.

Example:
Animal animal = new Dog();
animal.sound();

Resolution:
Happens at runtime.

Based on:
Actual object type, not reference type.

This is true polymorphism.

---

## 4. Dynamic Method Dispatch

At runtime:
JVM determines which overridden method to call.

Mechanism:
- Based on object’s actual type
- Enables flexible and extensible systems

Example:
Payment payment = new CreditCardPayment();
payment.process();

---

## 5. Reference Type vs Object Type (Very Important)

Example:
Animal animal = new Dog();

- Reference type: Animal
- Object type: Dog

Rules:
- Accessible methods → based on reference type
- Executed overridden method → based on object type

This is a common interview trap.

---

## 6. Polymorphism and Extensibility

Polymorphism allows:
- Adding new implementations without modifying existing code
- Open-Closed Principle (Open for extension, closed for modification)

Example:
Adding new payment method without changing payment logic.

---

## 7. Polymorphism in Backend Systems

Used heavily in:
- Strategy pattern
- Dependency injection
- Service interfaces
- Spring beans
- REST controllers

Example:
Multiple implementations of NotificationService.

---

## 8. Limitations

Polymorphism does not apply to:
- Static methods
- Private methods
- Constructors

Static methods are resolved at compile time.

---

## 9. Common Design Mistakes

- Calling subclass-specific methods via parent reference
- Overusing instanceof
- Violating Liskov Substitution Principle
- Confusing overloading with overriding

---

## 10. Interview-Safe Summary

> Polymorphism allows a common interface to represent multiple implementations, enabling runtime flexibility and extensibility in backend systems.
