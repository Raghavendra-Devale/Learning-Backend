

# ✅ LEVEL 0 – Academic

### 1. What is inheritance?

Inheritance is a mechanism where one class (child/subclass) acquires properties and behavior of another class (parent/superclass).

It represents an **IS-A relationship**.

Example:

```
Dog IS-A Animal
```

---

### 2. What is the syntax of inheritance in Java?

```java
class Animal {
    void eat() {}
}

class Dog extends Animal {
    void bark() {}
}
```

---

### 3. What is the purpose of inheritance?

* Code reusability
* Runtime polymorphism
* Logical hierarchy modeling
* Method overriding

---

### 4. What is method overriding?

When a child class provides its own implementation of a parent class method with the same signature.

```java
@Override
void eat() {
   System.out.println("Dog eats bones");
}
```

---

### 5. What is `super` keyword?

Used to:

* Access parent class constructor → `super()`
* Access parent methods → `super.method()`
* Access parent variables → `super.variable`

---

# ✅ LEVEL 1 – Fresher

### 1. What is IS-A relationship?

If class B extends class A, then B **IS-A** A.

Example:

```
Car IS-A Vehicle
```

---

### 2. Inheritance vs Composition

| Inheritance            | Composition         |
| ---------------------- | ------------------- |
| IS-A                   | HAS-A               |
| Tight coupling         | Loose coupling      |
| Compile-time structure | Runtime flexibility |
| Fragile                | More maintainable   |

Example:

```
Car HAS-A Engine  (Composition)
Dog IS-A Animal   (Inheritance)
```

---

### 3. Why Java does not support multiple inheritance of classes?

To avoid ambiguity and the **diamond problem**.

---

### 4. What is diamond problem?

![Image](https://cdn-media-1.freecodecamp.org/images/1%2AQVZomxLNxnRYhm9gGIfYyw.png)

![Image](https://textbooks.cs.ksu.edu/cc210/images/13-inherit/12.7.x.7.diamond_wiki.png)

![Image](https://d14qv6cm1t62pm.cloudfront.net/ccbp-website/Blogs/home/diamond-problem-in-java-explained-with-examples-and-solutions-image-1.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2Azw4KUCa_4YXpld4alY1iJw.png)

When two classes inherit from the same parent and a child inherits from both — ambiguity occurs about which parent method to use.

Java avoids this by:

* Not allowing multiple class inheritance
* Allowing multiple interface inheritance

---

### 5. Can constructors be inherited?

No.
Constructors are not inherited, but they are called using `super()`.

Execution order:

```
Parent constructor → Child constructor
```

---

# ✅ LEVEL 2 – 1–2 Years Experience

### 1. What is fragile base class problem?

If the parent class changes, it may unintentionally break child classes.

Example:

* Parent changes internal method logic
* Child overriding behavior breaks

---

### 2. Why is inheritance tight coupling?

Child depends heavily on parent’s internal implementation.

Any change in parent impacts child.

---

### 3. What happens if parent method changes?

* Child behavior may change unexpectedly
* Overridden methods may behave inconsistently
* Can introduce runtime bugs

---

### 4. Method Overriding Rules

* Same method signature
* Cannot reduce visibility
* Cannot throw broader checked exception
* Return type must be same or covariant
* Cannot override final/static methods

---

### 5. Can private methods be overridden?

No.

Private methods are not visible to subclasses.

---

### 6. What is covariant return type?

Child method can return a more specific type than parent method.

```java
class Animal {
    Animal getAnimal() {}
}

class Dog extends Animal {
    @Override
    Dog getAnimal() {}   // Allowed
}
```

---

### 7. Why should inheritance not be used just for reuse?

Because:

* It creates tight coupling
* Breaks encapsulation
* Reduces flexibility
* Makes maintenance harder

Better alternative → Composition

---

# ✅ LEVEL 3 – 2–3 Years Experience

### 1. When should you prefer composition over inheritance?

* Behavior can change dynamically
* No true IS-A relationship
* Need flexibility
* Avoid tight coupling

Modern frameworks prefer composition.

---

### 2. How does inheritance break encapsulation?

Child class gains access to protected members.
Parent internal changes affect child.

---

### 3. How can inheritance cause concurrency issues?

If parent is not thread-safe and child adds state:

* Inconsistent behavior
* Broken synchronization logic

---

### 4. What is Liskov Substitution Principle?

Defined by Barbara Liskov.

> Subclasses should be replaceable for their base classes without altering correctness.

If `Dog extends Animal`, then:

```java
Animal a = new Dog();
```

Should behave correctly.

---

### 5. How does inheritance affect maintainability?

* Deep hierarchies are hard to debug
* Parent changes ripple down
* Hard to refactor safely

---

### 6. How do frameworks safely use inheritance?

Examples:

* Spring Framework
* Hibernate

They:

* Use abstract base classes
* Keep methods protected carefully
* Prefer interfaces
* Combine inheritance with composition

---

# ✅ Senior / Twisted Questions

### 1. Can inheritance exist without polymorphism?

Yes.
If no method is overridden, inheritance still exists but polymorphism does not.

---

### 2. Is inheritance required for code reuse?

No.
Composition, delegation, and utility classes also enable reuse.

---

### 3. What happens if overridden method throws broader exception?

Compilation error.

Child cannot throw broader checked exception than parent.

---

### 4. Why are deep inheritance hierarchies dangerous?

![Image](https://miro.medium.com/1%2ALfEd2I7Kn2LrAtYxibYACA.jpeg)

![Image](https://www.researchgate.net/publication/221553946/figure/fig1/AS%3A340197008003086%401458120695939/UML-class-diagram-of-the-inheritance-hierarchy-of-our-design-approach-The-classes-used.png)

![Image](https://staff.fnwi.uva.nl/a.j.p.heck/Courses/JAVAcourse/ch3/lettertree.gif)

![Image](https://staff.fnwi.uva.nl/a.j.p.heck/Courses/JAVAcourse/ch3/inheritance.gif)

Because:

* Hard to understand
* High coupling
* Ripple effect changes
* Violates Single Responsibility Principle

---

### 5. Can inheritance increase memory footprint?

Yes.

Each subclass object includes parent class fields.
Deep hierarchy → more fields → larger object size.

---

### 6. How does `final` method affect inheritance?

* Cannot be overridden
* Prevents polymorphism for that method

---

### 7. Can static methods be overridden?

No.

Static methods are hidden, not overridden.

---

# 🚫 Common Traps (Interview Awareness)

* Inheritance ≠ just reuse
* IS-A must be logical
* Constructors are not inherited
* Java does NOT support multiple class inheritance
* Overriding rules must be correct

---

# 🎯 Interview-Safe Summary

> Inheritance establishes an IS-A relationship and enables runtime polymorphism. However, it introduces tight coupling and fragility. Modern backend systems often prefer composition to achieve flexibility and maintainability while reducing the risks associated with deep inheritance hierarchies.

---