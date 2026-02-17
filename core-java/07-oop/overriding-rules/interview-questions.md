

# ✅ LEVEL 0 – Academic

### 1️⃣ What is method overriding?

Method overriding happens when a subclass provides its own implementation of a parent class method with the **same signature**.

It enables runtime polymorphism.

---

### 2️⃣ Rules for overriding

* Same method name
* Same parameter list
* Cannot reduce visibility
* Cannot throw broader checked exceptions
* Return type must be same or covariant
* Cannot override `final`, `static`, or `private` methods

---

### 3️⃣ Can constructors be overridden?

No.
Constructors are not inherited, so they cannot be overridden.

---

### 4️⃣ What is covariant return type?

Child method can return a **subtype** of the parent’s return type.

```java
class Parent {
    Animal get();
}

class Child extends Parent {
    Dog get(); // valid if Dog extends Animal
}
```

---

# ✅ LEVEL 1 – Fresher

### 1️⃣ Can access modifier be reduced?

No.

You can widen visibility (protected → public), but not reduce it.

---

### 2️⃣ Can final methods be overridden?

No.
`final` prevents overriding to protect behavior.

---

### 3️⃣ Can static methods be overridden?

No.
Static methods are **hidden**, not overridden.

---

### 4️⃣ What happens if signature changes?

It becomes **method overloading**, not overriding.

---

### 5️⃣ What is method hiding?

When a subclass defines a static method with the same signature as the parent’s static method.

Resolved at compile time.

---

# ✅ LEVEL 2 – 1–2 YOE

### 1️⃣ Why can't child throw broader checked exception?

Because it would break polymorphism.

If parent reference doesn’t expect that exception, substitutability fails.

---

### 2️⃣ Why can't visibility be reduced?

Because parent contract promises a certain access level.

Reducing it would violate Liskov Substitution Principle.

---

### 3️⃣ Overloading vs Overriding

| Overloading             | Overriding           |
| ----------------------- | -------------------- |
| Same method name        | Same signature       |
| Different parameters    | Same parameters      |
| Compile-time            | Runtime              |
| No inheritance required | Requires inheritance |

---

### 4️⃣ What if parent method is private?

Private methods are not inherited, so child cannot override them.

If child defines same signature, it's a new method.

---

### 5️⃣ Why use `@Override`?

* Compile-time safety
* Prevents accidental overloading
* Improves readability

Always recommended.

---

### 6️⃣ Can return type change?

Yes, but only to a **subtype** (covariant return).

Not to an unrelated type.

---

# ✅ LEVEL 3 – 2–3 YOE

### 1️⃣ How overriding relates to LSP?

Overridden method must:

* Preserve behavior contract
* Not strengthen preconditions
* Not weaken postconditions

Otherwise substitution fails.

---

### 2️⃣ How wrong overriding breaks APIs?

If subclass:

* Changes expected behavior
* Throws unexpected exceptions
* Breaks invariants

Client code using parent reference may fail unexpectedly.

---

### 3️⃣ How JVM performs dynamic dispatch?

* Uses virtual method table (vtable)
* Resolves method at runtime
* JIT may inline optimized calls

---

### 4️⃣ How overriding introduces security risks?

If subclass:

* Removes validation logic
* Weakens authorization checks
* Bypasses synchronization

It can break invariants or expose vulnerabilities.

---

### 5️⃣ What is bridge method? (Advanced)

When using generics, JVM creates **synthetic bridge methods** to maintain polymorphism after type erasure.

Ensures overridden generic methods still behave correctly at runtime.

---

### 6️⃣ How generics affect overriding?

Due to type erasure:

* Method signatures must match after erasure
* May generate bridge methods
* Return type covariance works with generics

---

# ✅ Senior / Twisted

### 1️⃣ Can you override and throw RuntimeException?

Yes.

Unchecked exceptions are allowed.

---

### 2️⃣ What if parent throws no exception?

Child cannot throw new checked exceptions.

But can throw RuntimeException.

---

### 3️⃣ Can abstract method override concrete method?

Yes.

If subclass declares parent method abstract, then subclass must be abstract.

---

### 4️⃣ Can concrete method override abstract method?

Yes.

That’s the normal case — providing implementation.

---

### 5️⃣ What if parent method is final?

Cannot override. Compile-time error.

---

### 6️⃣ Can synchronized modifier be changed?

Yes.

But removing synchronization may break thread-safety guarantees and violate LSP.

---

### 7️⃣ What if return type is incompatible?

Compilation error.

Return type must be same or subtype.

---

# 🎯 Interview-Safe Explanation (Polished)

> Method overriding enables runtime polymorphism but must respect the parent contract by maintaining visibility, checked exception rules, and compatible return types. This ensures safe substitutability and predictable behavior in large systems.

---

