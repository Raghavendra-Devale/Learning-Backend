# Default and Static Methods  Interview Questions

---

# 🔹 0 Level

---

### 1️⃣ What is a default method?

A default method is a method defined inside an interface with a concrete implementation using the `default` keyword.

It allows interfaces to have behavior along with method declarations.

---

### 2️⃣ Why were default methods introduced?

Default methods were introduced in Java 8 to support backward compatibility.

They allow new methods to be added to existing interfaces without breaking implementing classes.

This enables API evolution.

---

# 🔹 Fresher Level

---

### 1️⃣ Can default methods be overridden?

Yes.

Implementing classes can override default methods just like normal methods.

---

### 2️⃣ Can interface have multiple default methods?

Yes.

An interface can have multiple default methods as long as there is only one abstract method if it is intended to be a functional interface.

Default methods do not count as abstract methods.

---

### 3️⃣ What is diamond problem?

The diamond problem occurs when a class implements two interfaces that contain the same default method.

Java cannot decide which implementation to use.

---

### 4️⃣ How do you resolve diamond problem?

The class must override the conflicting method explicitly.

Example:

```java
@Override
public void show() {
    A.super.show();
}
```

The class chooses which interface implementation to call.

---

### 5️⃣ What is static method in interface?

A static method in an interface is a method with implementation that belongs to the interface itself.

It is accessed using the interface name and is not inherited by implementing classes.

---

# 🔹 1–2 YOE

---

### 1️⃣ Are static methods inherited?

No.

Static methods in interfaces are not inherited by implementing classes.

They must be called using the interface name.

---

### 2️⃣ Can static methods be overridden?

No.

Static methods belong to the interface and cannot be overridden.

They can only be hidden if defined again in a class, but that is not overriding.

---

### 3️⃣ Why are default methods important for API evolution?

They allow new functionality to be added to interfaces without breaking existing implementations.

This was critical when Java 8 added methods like `stream()` to Collection.

It preserves backward compatibility.

---

### 4️⃣ What happens if class implements two interfaces with same default method?

Compilation error occurs due to ambiguity.

The class must override the method and explicitly choose which implementation to use.

---

# 🔹 2–3 YOE

---

### 1️⃣ How does Java resolve method conflicts?

Method resolution priority:

1. Class methods have highest priority.
2. If no class method, most specific interface default method is chosen.
3. If conflict exists between interfaces, class must override.

This ensures deterministic behavior.

---

### 2️⃣ When would you use default method in backend design?

Default methods are useful when:

* Evolving APIs without breaking clients
* Providing common reusable behavior
* Defining template-like logic in interfaces

They are helpful in framework and library design.

---

### 3️⃣ Difference between abstract class and default method?

Abstract class:

* Can have state (instance variables)
* Can have constructors
* Supports partial implementation
* Single inheritance

Interface with default method:

* Cannot have instance state
* No constructors
* Supports multiple inheritance
* Used mainly for behavior contracts

---

### 4️⃣ Can default method call private method inside interface? (Java 9+)

Yes.

From Java 9 onwards, interfaces can have private methods.

Default methods can call private helper methods inside the same interface.

This helps in code reuse within the interface.

---