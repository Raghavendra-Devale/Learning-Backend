
# ✅ LEVEL 0 – Academic

### 1️⃣ What is inheritance?

Inheritance allows a class to acquire properties and behavior of another class.

It establishes an **IS-A** relationship.

---

### 2️⃣ Syntax in Java

```java
class Child extends Parent {
}
```

---

### 3️⃣ Purpose of inheritance

* Code reuse
* Runtime polymorphism
* Establish hierarchy

But reuse is not the primary design goal — modeling behavior is.

---

### 4️⃣ What is method overriding?

When a subclass provides its own implementation of a parent method with the same signature.

Enables runtime polymorphism.

---

### 5️⃣ What is `super` keyword?

Used to:

* Access parent class methods
* Call parent constructor
* Refer to parent fields

Example:

```java
super.display();
```

---

# ✅ LEVEL 1 – Fresher

### 1️⃣ What is IS-A relationship?

If `Dog extends Animal`, then:

> Dog **is a** Animal.

Inheritance must represent a true subtype relationship.

---

### 2️⃣ Inheritance vs Composition

| Inheritance          | Composition       |
| -------------------- | ----------------- |
| IS-A                 | HAS-A             |
| Tight coupling       | Loose coupling    |
| Compile-time binding | Flexible design   |
| Less flexible        | More maintainable |

Example:

```java
class Car {
    private Engine engine; // composition
}
```

---

### 3️⃣ Why no multiple inheritance of classes in Java?

To avoid ambiguity and complexity (diamond problem).

Java supports multiple inheritance via interfaces instead.

---

### 4️⃣ What is diamond problem?

Occurs when a class inherits from two classes having same method.

Ambiguity: which method to use?

Java avoids it by not allowing multiple class inheritance.

---

### 5️⃣ Can constructors be inherited?

No.

Constructors are not inherited, but parent constructor is called using `super()`.

---

# ✅ LEVEL 2 – 1–2 YOE

### 1️⃣ What is fragile base class problem?

When changes in parent class break child classes unexpectedly.

Subclasses depend heavily on parent implementation details.

---

### 2️⃣ Why is inheritance tight coupling?

Because:

* Child depends on parent’s internal implementation
* Parent changes ripple downward
* Hard to refactor independently

---

### 3️⃣ What happens if parent method changes?

* Child behavior may break
* Overridden logic may conflict
* Polymorphic contracts may fail

---

### 4️⃣ Method overriding rules

* Same method signature
* Cannot reduce visibility
* Cannot throw broader checked exceptions
* Return type can be covariant
* Cannot override final or static methods

---

### 5️⃣ Can private methods be overridden?

No.

Private methods are not visible to subclasses.

---

### 6️⃣ What is covariant return type?

Overridden method can return subtype of parent method return type.

Example:

```java
Parent get();
Child get(); // valid
```

---

### 7️⃣ Why inheritance should not be used just for reuse?

Because:

* It forces IS-A relationship
* Creates tight coupling
* Makes hierarchy rigid

Reuse via composition is safer.

---

# ✅ LEVEL 3 – 2–3 YOE

### 1️⃣ When prefer composition over inheritance?

* When relationship is HAS-A
* When behavior may change
* When flexibility is required
* In service-layer/backend design

Modern systems favor composition.

---

### 2️⃣ How inheritance breaks encapsulation?

Child class gains access to protected members and internal behavior.

This exposes implementation details to subclasses.

---

### 3️⃣ How inheritance can cause concurrency issues?

If parent class is not thread-safe:

* Subclass may override methods incorrectly
* Synchronization logic may be bypassed
* Shared mutable state becomes unsafe

---

### 4️⃣ What is Liskov Substitution Principle (LSP)?

Subtypes must be replaceable for their base types without breaking behavior.

If `Square extends Rectangle` breaks expectations, LSP is violated.

---

### 5️⃣ How inheritance affects maintainability?

Deep hierarchies:

* Hard to trace logic
* Hard to debug
* Changes have ripple effects

---

### 6️⃣ How frameworks safely use inheritance?

Frameworks often:

* Use template method pattern
* Provide abstract base classes
* Control extension points carefully
* Mark critical methods as final

Example: Servlet API, Spring base classes.

---

# ✅ Senior / Twisted

### 1️⃣ Can inheritance exist without polymorphism?

Technically yes (if methods not overridden),
but its real power comes from polymorphism.

---

### 2️⃣ Is inheritance required for reuse?

No.

Composition and delegation can achieve reuse.

---

### 3️⃣ What if overridden method throws broader exception?

Not allowed for checked exceptions.

It would break polymorphism.

---

### 4️⃣ Why deep hierarchies are dangerous?

* Fragile
* Hard to reason about
* Violates SRP
* Ripple effects

---

### 5️⃣ Can inheritance increase memory footprint?

Yes.

If parent has unnecessary fields, every subclass object carries them.

---

### 6️⃣ How does final method affect inheritance?

Final methods:

* Cannot be overridden
* Protect behavior
* Preserve invariants

---

### 7️⃣ Can static methods be overridden?

No.

Static methods are hidden, not overridden.

---

# 🎯 Interview-Safe Summary

> Inheritance models an IS-A relationship and enables runtime polymorphism, but it creates tight coupling between classes. Because of fragility and reduced flexibility, modern backend systems prefer composition over deep inheritance hierarchies.

---
