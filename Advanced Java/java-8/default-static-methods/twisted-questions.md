# Default & Static Methods  Twisted Questions

---

### 1️⃣ Can interface have constructor?

**Answer:**
No.

**Why?**

Interfaces cannot have constructors because:

* They cannot be instantiated directly.
* They do not maintain instance state.

Constructors are meant for initializing object state, which interfaces do not have.

---

### 2️⃣ Can static method be overridden?

**Answer:**
No.

**Why?**

Static methods belong to the interface itself, not to implementing classes.

They are not inherited, so they cannot be overridden.

They must be accessed using:

```java
InterfaceName.methodName();
```

---

### 3️⃣ Can you call static interface method using implementing class?

**Answer:**
No.

**Why?**

Static interface methods are not inherited by implementing classes.

This is invalid:

```java
MyClass.methodName(); // Not allowed if method is static in interface
```

Correct usage:

```java
MyInterface.methodName();
```

---

### 4️⃣ What happens if class extends a class and implements an interface with same method?

**Answer:**
Class method takes precedence.

**Why?**

Method resolution order in Java:

1. Class methods have highest priority.
2. Then interface default methods.

If a superclass already provides an implementation, it overrides the interface default method automatically.

---

### 5️⃣ Does default method break multiple inheritance rule?

**Answer:**
No.

**Why?**

Java does not allow multiple inheritance of classes, but it allows multiple inheritance of interfaces.

If two interfaces provide the same default method, Java forces the implementing class to resolve the conflict explicitly.

This prevents ambiguity and maintains type safety.

---

End of Twisted Questions.
