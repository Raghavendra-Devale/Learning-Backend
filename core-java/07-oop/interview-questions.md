## Core OOP Concepts

### Q1. What is Object-Oriented Programming?
**Answer:**
OOP is a programming approach that models systems using objects that encapsulate state and behavior, enabling modular, maintainable, and extensible designs.

---

### Q2. Difference between Class and Object?
**Answer:**
A class is a blueprint loaded once by the JVM, while an object is a runtime instance created in heap memory.

---

## Encapsulation (VERY IMPORTANT)

### Q3. What is encapsulation?
**Answer:**
Encapsulation is the practice of controlling access to data and enforcing rules to protect an object’s internal state.

---

### Q4. Why is encapsulation critical in backend systems?
**Answer:**
Backend systems handle shared and sensitive data. Encapsulation prevents invalid state changes, enforces validation, and reduces concurrency issues.

---

### Q5. Is encapsulation just about private variables?
**Answer:**
No. It is about controlling behavior and access, not just restricting visibility.

---

## Inheritance vs Composition

### Q6. What is inheritance?
**Answer:**
Inheritance allows a class to reuse and extend behavior from another class using the `extends` keyword.

---

### Q7. Why is inheritance considered risky?
**Answer:**
Inheritance creates tight coupling and fragile hierarchies, where changes in parent classes can break child classes.

---

### Q8. Why is composition preferred over inheritance?
**Answer:**
Composition avoids tight coupling, improves flexibility, and allows behavior changes without modifying class hierarchies.

---

### Q9. Give a real backend example of composition.
**Answer:**
An `OrderService` having a `PaymentService` is better than extending it, as responsibilities remain separated and testable.

---

## Polymorphism

### Q10. What is polymorphism?
**Answer:**
Polymorphism allows a reference of a parent type or interface to point to different implementations, with behavior decided at runtime.

---

### Q11. What is dynamic method dispatch?
**Answer:**
It is the JVM mechanism that resolves overridden methods at runtime based on the actual object type.

---

### Q12. Can polymorphism exist without inheritance?
**Answer:**
Yes. Interfaces enable polymorphism without class inheritance.

---

## Abstraction

### Q13. What is abstraction?
**Answer:**
Abstraction exposes what a class does while hiding how it does it.

---

### Q14. Interface vs Abstract Class?
**Answer:**
Interfaces define contracts and allow multiple inheritance. Abstract classes share base behavior. Interfaces are preferred for loose coupling.

---

## Overriding & Overloading (TRAPS)

### Q15. Difference between method overloading and overriding?
**Answer:**
Overloading is resolved at compile time, overriding at runtime.

---

### Q16. Can we override static methods?
**Answer:**
No. Static methods are hidden, not overridden.

---

### Q17. Can we override private methods?
**Answer:**
No. Private methods are not visible to subclasses.

---

### Q18. Can we reduce visibility while overriding?
**Answer:**
No. Visibility can only be increased, not reduced.

---

## OOP + Multithreading

### Q19. Why is encapsulation important in multi-threaded systems?
**Answer:**
It prevents uncontrolled access to shared state, reducing race conditions and concurrency bugs.

---

## OOP + Spring Framework

### Q20. Why does Spring prefer interfaces?
**Answer:**
Spring uses interfaces to enable loose coupling, dependency injection, easier testing, and runtime swapping of implementations.

---

### Q21. How does Spring use OOP principles?
**Answer:**
Spring uses abstraction via interfaces, encapsulation in services, polymorphism for multiple implementations, and composition through dependency injection.

---

## Design & Senior-Level Questions

### Q22. Is OOP always the best approach?
**Answer:**
No. OOP works well for complex systems with behavior and state, but functional or procedural approaches may be simpler for some problems.

---

### Q23. Why not make everything public?
**Answer:**
Public access breaks encapsulation, allows invalid state changes, and increases maintenance and bug risk.

---

### Q24. Why not use static everywhere?
**Answer:**
Static creates global shared state, leading to concurrency issues, memory leaks, and poor testability.

---

## Common Interview Traps & Pitfalls

❌ Encapsulation = private variables  
❌ Inheritance = best reuse technique  
❌ Polymorphism = overloading  
❌ Interfaces are used for security  
❌ Static methods can be overridden  

---

## One Interview-Safe Summary

> “OOP helps build backend systems that are safe, flexible, and maintainable by protecting state through encapsulation, enabling extensibility through abstraction and polymorphism, and favoring composition over inheritance.”

---
