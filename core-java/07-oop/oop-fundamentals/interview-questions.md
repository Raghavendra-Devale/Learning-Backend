
# ✅ LEVEL 0 – Academic / Beginner

### 1️⃣ What is OOP?

OOP (Object-Oriented Programming) is a paradigm that organizes software around **objects**, which bind **data (state)** and **functions (behavior)** together.

---

### 2️⃣ Four Pillars of OOP

* **Encapsulation** – Hiding internal state and exposing controlled access.
* **Abstraction** – Hiding implementation details, showing only essentials.
* **Inheritance** – Reusing behavior from another class.
* **Polymorphism** – Same interface, different implementation.

---

### 3️⃣ What is a class?

A **blueprint/template** that defines structure (variables) and behavior (methods).

---

### 4️⃣ What is an object?

A **runtime instance of a class** with:

* State
* Behavior
* Identity

---

### 5️⃣ Class vs Object

| Class                | Object                    |
| -------------------- | ------------------------- |
| Blueprint            | Real instance             |
| Logical structure    | Physical entity in memory |
| No memory for values | Has memory allocated      |

---

# ✅ LEVEL 1 – Fresher

### 1️⃣ Why is OOP better than procedural programming?

Because it:

* Controls state mutation
* Improves modularity
* Makes systems easier to maintain and extend

Procedural code often becomes hard to manage as complexity grows.

---

### 2️⃣ What problem does OOP solve?

It solves the problem of **uncontrolled shared state** and **spaghetti code** in large systems.

---

### 3️⃣ What is state and behavior?

* **State** → variables (data)
* **Behavior** → methods (actions)
  Together they define an object.

---

### 4️⃣ What is identity?

Even if two objects have same state, they are different in memory.

Example:

```java
new User("Raghav") != new User("Raghav");
```

---

### 5️⃣ Is class an object in Java?

Yes. Every class in Java is an object of `java.lang.Class`.

But primitives (int, boolean) are not objects.

---

# ✅ LEVEL 2 – 1–2 YOE

### 1️⃣ Why is binding state and behavior important?

Because it:

* Prevents invalid state
* Protects invariants
* Reduces external mutation

---

### 2️⃣ What happens if encapsulation is broken?

* Invariants break
* Harder debugging
* Increased coupling
* Concurrency bugs

---

### 3️⃣ Which pillar is most important in backend design?

Encapsulation.

Backend systems mostly suffer from shared mutable state, not lack of inheritance.

---

### 4️⃣ Why is inheritance often misused?

Because developers use it for:

* Code reuse instead of behavior modeling
* Forcing IS-A relationships that aren’t real

It creates tight coupling.

---

### 5️⃣ What is tight coupling?

When classes depend heavily on each other’s implementation details.

Hard to change one without breaking others.

---

### 6️⃣ How does OOP support layered architecture?

By:

* Separating concerns (Controller, Service, Repository)
* Encapsulating responsibilities
* Using interfaces for abstraction

---

# ✅ LEVEL 3 – 2–3 YOE

### 1️⃣ How does OOP help scalability?

* Encapsulation limits side effects
* Interfaces allow swapping implementations
* Dependency injection enables flexible architecture

---

### 2️⃣ When does OOP increase complexity?

* Deep inheritance trees
* Over-engineering abstractions
* Too many small classes
* Excessive patterns

---

### 3️⃣ How do objects protect invariants?

By:

* Making fields private
* Validating data in constructors/setters
* Not exposing mutable internals

---

### 4️⃣ Why prefer composition over inheritance?

Composition:

* Reduces coupling
* Increases flexibility
* Follows "has-a" instead of forcing "is-a"

Example:

```java
class Car {
    private Engine engine;
}
```

---

### 5️⃣ How does OOP enable dependency injection?

Because:

* Behavior is abstracted behind interfaces
* Objects receive dependencies instead of creating them

---

### 6️⃣ How poorly designed objects cause concurrency issues?

* Exposing mutable state
* Sharing state without synchronization
* Breaking encapsulation

---

# ✅ Senior / Twisted Questions

### 1️⃣ If OOP is good, why do functional languages exist?

Because OOP struggles with:

* Shared mutable state
* Concurrency
* Complex inheritance

Functional programming reduces side effects.

---

### 2️⃣ Biggest flaw of OOP?

Encourages mutable state by default.

---

### 3️⃣ Is everything in Java an object?

No. Primitive types are not objects.

---

### 4️⃣ Can OOP exist without inheritance?

Yes.

Encapsulation + abstraction + polymorphism are enough.

Inheritance is optional.

---

### 5️⃣ How does OOP affect memory management?

Objects are heap allocated.
Poor object design → memory bloat & GC pressure.

---

### 6️⃣ Can breaking encapsulation cause race conditions?

Yes.

If internal mutable state is exposed, multiple threads can modify it unpredictably.

---

### 7️⃣ Why are large inheritance hierarchies dangerous?

* Hard to understand
* Fragile base class problem
* Changes ripple downward
* Violates Open/Closed Principle

---

# 🎯 Interview-Safe Explanation (Polished)

> OOP organizes software by binding state and behavior into objects, enforcing controlled access to state. This improves modularity, reduces unintended side effects, and makes large systems easier to evolve and maintain.

---
