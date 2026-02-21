

# ✅ LEVEL 0 – Academic

### 1️⃣ What is abstraction?

Abstraction means **exposing only essential behavior while hiding implementation details**.

User knows *what* an object does, not *how* it does it.

---

### 2️⃣ How is abstraction achieved in Java?

* Interfaces
* Abstract classes

Both define contracts without exposing full implementation.

---

### 3️⃣ What is an abstract class?

A class that:

* Cannot be instantiated
* Can have abstract and concrete methods
* Can have state (fields)

```java
abstract class Payment {
    abstract void process();
}
```

---

### 4️⃣ What is an interface?

A contract that:

* Defines behavior
* Can be implemented by multiple classes
* Supports multiple inheritance

```java
interface PaymentProcessor {
    void process();
}
```

---

# ✅ LEVEL 1 – Fresher

### 1️⃣ Abstraction vs Encapsulation

| Abstraction                  | Encapsulation               |
| ---------------------------- | --------------------------- |
| Hides implementation details | Restricts access to state   |
| Focuses on behavior contract | Focuses on state protection |

Abstraction = what
Encapsulation = how state is protected

---

### 2️⃣ Can abstract class have constructor?

Yes.

Used to initialize common state for subclasses.

---

### 3️⃣ Can interface have method implementation?

Yes (since Java 8):

* `default` methods
* `static` methods
* `private` methods (Java 9+)

---

### 4️⃣ Can interface have variables?

Yes.

But they are implicitly:

* `public`
* `static`
* `final`

They are constants.

---

### 5️⃣ Can abstract class implement interface?

Yes.

It may:

* Provide partial implementation
* Leave remaining methods abstract

---

# ✅ LEVEL 2 – 1–2 YOE

### 1️⃣ Interface vs Abstract Class

| Interface                    | Abstract Class       |
| ---------------------------- | -------------------- |
| Pure contract                | Partial abstraction  |
| Multiple inheritance         | Single inheritance   |
| No instance state (normally) | Can have state       |
| More flexible                | More tightly coupled |

---

### 2️⃣ When use interface over abstract class?

* When behavior is a contract
* When multiple implementations expected
* When flexibility is required
* In service layer/backend APIs

---

### 3️⃣ Why multiple interface inheritance allowed?

Because interfaces don’t carry implementation state traditionally, avoiding ambiguity like diamond problem in classes.

---

### 4️⃣ What are default methods?

Methods with implementation inside interface.

```java
default void log() {
    System.out.println("Logging");
}
```

---

### 5️⃣ What problem did default methods solve?

Backward compatibility.

They allowed adding new methods to interfaces without breaking existing implementations (e.g., Java Collections framework in Java 8).

---

### 6️⃣ Can interface have private methods?

Yes (Java 9+).

Used to avoid code duplication inside default methods.

---

# ✅ LEVEL 3 – 2–3 YOE

### 1️⃣ How abstraction enables dependency injection?

Code depends on abstraction (interface), not implementation.

```java
public OrderService(PaymentProcessor processor)
```

Implementation can be injected at runtime.

---

### 2️⃣ Why interfaces preferred in Spring?

* Loose coupling
* Easy mocking for testing
* JDK dynamic proxies work with interfaces
* Swappable implementations

Spring heavily relies on interface-based programming.

---

### 3️⃣ Risks of deep abstract class hierarchies?

* Fragile base class problem
* Tight coupling
* Hard to modify
* Violates SRP

Abstract class trees can become rigid quickly.

---

### 4️⃣ How abstraction supports Open-Closed Principle?

You can add new implementations without modifying existing client code.

Client depends on abstraction only.

---

### 5️⃣ Should every class have an interface?

No.

Create interface only when:

* Multiple implementations expected
* External exposure required
* Testing/mocking needed

Otherwise, unnecessary abstraction increases complexity.

---

### 6️⃣ How default methods affect API evolution?

They allow:

* Extending interfaces safely
* Adding behavior without breaking consumers

But excessive default logic can blur responsibility boundaries.

---

# ✅ Senior / Twisted

### 1️⃣ Can abstraction exist without interfaces?

Yes.

Through:

* Abstract classes
* Encapsulation
* Functional programming (higher-order functions)

---

### 2️⃣ Is abstract class more powerful than interface?

In terms of structure:

* Abstract class can hold state and constructors

But interfaces provide more flexibility due to multiple inheritance.

Neither is “better” universally.

---

### 3️⃣ Why default methods introduced in Java 8?

To evolve core APIs (like `Collection`) without breaking millions of existing implementations.

---

### 4️⃣ Can abstraction increase complexity?

Yes.

Over-abstraction:

* Too many interfaces
* Hard navigation
* Reduced readability

Abstraction must serve clarity, not ceremony.

---

### 5️⃣ What if two interfaces have same default method?

```java
class MyClass implements A, B
```

Compiler forces override to resolve ambiguity.

---

### 6️⃣ How JVM handles interface method dispatch?

Uses dynamic dispatch via:

* Interface method table
* JIT optimizations
* Similar to virtual method resolution

---

### 7️⃣ Can an interface extend another interface?

Yes.

Supports multiple inheritance.

```java
interface B extends A {}
```

---

# 🎯 Interview-Safe Explanation (Polished)

> Abstraction defines a contract that exposes essential behavior while hiding implementation details. By programming to abstractions like interfaces, backend systems achieve loose coupling, extensibility, and easier testing through dependency injection.

---
