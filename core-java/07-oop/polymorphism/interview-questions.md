

# ✅ LEVEL 0 – Academic

### 1️⃣ What is polymorphism?

Polymorphism means **one interface, many implementations**.

It allows a parent reference to call methods of different child objects.

---

### 2️⃣ Types of polymorphism

* **Compile-time polymorphism** → Method overloading
* **Runtime polymorphism** → Method overriding

---

### 3️⃣ What is method overloading?

Same method name, different parameter list, resolved at compile time.

```java
add(int a, int b)
add(double a, double b)
```

---

### 4️⃣ What is method overriding?

Subclass provides its own implementation of a parent method with same signature.

Resolved at runtime.

---

# ✅ LEVEL 1 – Fresher

### 1️⃣ Overloading vs Overriding

| Overloading          | Overriding             |
| -------------------- | ---------------------- |
| Same method name     | Same method signature  |
| Different parameters | Same parameters        |
| Compile-time         | Runtime                |
| Within same class    | Between parent & child |

---

### 2️⃣ What is runtime polymorphism?

Method call resolved based on **actual object type**, not reference type.

```java
Animal a = new Dog();
a.sound(); // Dog’s method executes
```

---

### 3️⃣ What is compile-time polymorphism?

Resolved during compilation.

Based on method signature.

---

### 4️⃣ Can static methods be overridden?

No.

Static methods are **hidden**, not overridden.

---

### 5️⃣ Can private methods be overridden?

No.

Private methods are not visible to subclasses.

---

### 6️⃣ What is dynamic method dispatch?

Mechanism where JVM decides at runtime which overridden method to execute based on actual object.

---

# ✅ LEVEL 2 – 1–2 YOE

### 1️⃣ Reference type vs Object type

```java
Animal a = new Dog();
```

* Reference type → Animal
* Object type → Dog

Reference determines:

* Accessible methods (compile-time)

Object determines:

* Executed method (runtime)

---

### 2️⃣ Which method executes with parent reference?

The **overridden method in child**, if it exists.

But only methods declared in reference type are accessible.

---

### 3️⃣ How polymorphism supports Open-Closed Principle?

You can:

* Add new implementations
* Without modifying existing code

Example:
Add new `PaymentProcessor` without changing caller logic.

---

### 4️⃣ Why overloading is not true polymorphism?

Because:

* No runtime behavior change
* No subtype substitution
* Resolved at compile time

It’s syntactic convenience, not behavioral polymorphism.

---

### 5️⃣ What happens if method is final?

Final methods:

* Cannot be overridden
* Disable runtime polymorphism for that method

---

### 6️⃣ Can constructors participate in polymorphism?

No.

Constructors are not inherited and are resolved at compile time.

---

# ✅ LEVEL 3 – 2–3 YOE

### 1️⃣ How polymorphism enables dependency injection?

Because:

* Code depends on interfaces
* Implementation injected at runtime
* Behavior swapped without modifying client

Example:

```java
PaymentService(PaymentProcessor processor)
```

---

### 2️⃣ How Spring uses polymorphism internally?

* Beans injected via interfaces
* Proxy objects for AOP
* Transaction management via dynamic proxies
* Strategy pattern usage

Spring relies heavily on runtime polymorphism.

---

### 3️⃣ Why is `instanceof` bad practice?

It:

* Breaks polymorphism
* Violates Open-Closed Principle
* Introduces conditional logic instead of delegation

If you need `instanceof`, design may be wrong.

---

### 4️⃣ How violating LSP breaks polymorphism?

If subclass changes expected behavior:

```java
Rectangle r = new Square();
```

If square breaks width/height logic → substitution fails.

Polymorphism depends on LSP.

---

### 5️⃣ How polymorphism reduces tight coupling?

Client depends on abstraction, not concrete class.

Switching implementation doesn’t change client code.

---

### 6️⃣ Performance cost of dynamic dispatch?

* Slight runtime overhead (virtual method table lookup)
* Usually negligible
* JVM optimizations (JIT inlining) reduce cost

Not a real-world concern in backend systems.

---

# ✅ Senior / Twisted

### 1️⃣ Can polymorphism exist without inheritance?

Yes.

Through:

* Interfaces
* Composition
* Functional interfaces / lambdas

Inheritance is not required.

---

### 2️⃣ How does polymorphism work with interfaces?

Any class implementing interface can be referenced by interface type.

```java
List<String> list = new ArrayList<>();
```

Runtime decides implementation.

---

### 3️⃣ Why static methods cannot be polymorphic?

Because:

* They belong to class, not object
* Resolved at compile time
* No dynamic dispatch

---

### 4️⃣ What if overridden method throws broader exception?

Not allowed for checked exceptions.

It would break substitutability.

---

### 5️⃣ How JVM resolves method calls internally?

* Uses virtual method table (vtable)
* Looks up method at runtime
* JIT may inline for performance

---

### 6️⃣ Can polymorphism cause subtle bugs?

Yes.

If:

* LSP violated
* Subclass changes expected behavior
* Overridden methods weaken contracts

---

### 7️⃣ Method hiding vs overriding

| Overriding         | Hiding                  |
| ------------------ | ----------------------- |
| Instance method    | Static method           |
| Runtime resolution | Compile-time resolution |
| True polymorphism  | Not polymorphism        |

---

# 🎯 Interview-Safe Explanation (Polished)

> Polymorphism allows a common abstraction to represent multiple implementations, enabling runtime method resolution based on the actual object type. It reduces coupling and supports extensibility in scalable backend systems.

---
