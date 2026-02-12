# Functional Interfaces — Interview Questions

---

# 🔹 0 Level

---

### 1️⃣ What is a functional interface?

A functional interface is an interface that contains exactly one abstract method (Single Abstract Method — SAM).

It may have multiple default and static methods, but only one abstract method.

---

### 2️⃣ Why was it introduced?

Functional interfaces were introduced in Java 8 to support lambda expressions.

A lambda provides the implementation of the single abstract method of a functional interface.

They enable functional programming style in Java.

---

### 3️⃣ Is @FunctionalInterface mandatory?

No, it is not mandatory.

However, it is recommended because:

* It ensures only one abstract method exists
* The compiler throws an error if another abstract method is added

It improves code safety and readability.

---

# 🔹 Fresher Level

---

### 1️⃣ Can functional interface have multiple methods?

It can have:

* One abstract method (mandatory)
* Multiple default methods
* Multiple static methods

But it cannot have more than one abstract method.

---

### 2️⃣ Can it have default methods?

Yes.

Default methods do not count as abstract methods.

Example:

```java
default void log() {
    System.out.println("Logging");
}
```

---

### 3️⃣ Can it have static methods?

Yes.

Static methods are allowed and do not affect functional interface rules.

---

### 4️⃣ What is effectively final variable?

A variable is effectively final if:

* It is assigned once
* Its value is not modified afterward

Lambdas can only access final or effectively final local variables.

---

### 5️⃣ Why does lambda require functional interface?

Because the compiler needs a target type.

A lambda provides the implementation of a single abstract method.
Without a functional interface, the compiler cannot determine which method the lambda implements.

---

# 🔹 1–2 YOE

---

### 1️⃣ Difference between anonymous class and lambda?

Lambda:

* Concise syntax
* Does not create a new scope
* `this` refers to enclosing class
* Cannot define extra methods

Anonymous class:

* Verbose
* Creates a new scope
* `this` refers to anonymous class
* Can define additional methods

---

### 2️⃣ What does `this` refer to inside lambda?

Inside a lambda, `this` refers to the enclosing class instance.

In anonymous classes, `this` refers to the anonymous class object.

---

### 3️⃣ Can lambda access instance variables?

Yes.

Lambdas can access:

* Instance variables
* Static variables
* Final or effectively final local variables

Instance variables do not need to be final.

---

### 4️⃣ What are built-in functional interfaces?

Common built-in interfaces in `java.util.function`:

* Predicate<T>
* Function<T, R>
* Consumer<T>
* Supplier<T>
* BiFunction<T, U, R>
* UnaryOperator<T>
* BinaryOperator<T>

These are widely used in Streams and backend code.

---

### 5️⃣ Where are Predicate and Function used in Streams?

Predicate is used in:

* `filter()`

Example:

```java
stream.filter(predicate);
```

Function is used in:

* `map()`

Example:

```java
stream.map(function);
```

---

# 🔹 2–3 YOE

---

### 1️⃣ Why are local variables in lambda required to be effectively final?

Because lambdas capture variables from the enclosing scope.

Allowing modification could cause inconsistent state and concurrency issues.

The effectively final rule ensures safe variable capture.

---

### 2️⃣ Is lambda compiled to anonymous class?

No.

Lambdas are not compiled into traditional anonymous inner classes.

They use JVM’s `invokedynamic` instruction.

---

### 3️⃣ How does JVM implement lambda internally?

The JVM uses the `invokedynamic` bytecode instruction.

At runtime, it dynamically creates an implementation of the functional interface.

This approach is more lightweight and optimized compared to anonymous classes.

---

### 4️⃣ When would you prefer anonymous class over lambda?

Prefer anonymous class when:

* Multiple methods need implementation
* You need a separate scope
* You need different `this` reference behavior
* You need to override default methods

Lambdas are suitable only for single-method interfaces.

---