# Lambda Expressions — Interview Questions 

---

# 🔹 0 Level

---

### 1️⃣ What is a lambda expression?

A lambda expression is a concise way to represent an anonymous function in Java.

It provides the implementation of a functional interface’s single abstract method (SAM).

---

### 2️⃣ Why were lambdas introduced in Java 8?

Lambdas were introduced to:

* Enable functional programming style
* Reduce boilerplate code
* Support Stream API
* Improve readability
* Replace verbose anonymous classes

They promote declarative programming.

---

### 3️⃣ Can lambda exist without functional interface?

No.

A lambda can only be used where a functional interface is expected.

Without a functional interface, the compiler cannot determine the target type.

---

# 🔹 Fresher Level

---

### 1️⃣ Explain lambda syntax.

Basic syntax:

```java
(parameters) -> expression
(parameters) -> { statements }
```

Key points:

* Parameter types can be inferred.
* Parentheses optional for single parameter.
* If using braces, `return` is mandatory.
* If single expression, return is implicit.

---

### 2️⃣ What is effectively final variable?

A variable is effectively final if:

* It is assigned once
* Its value is not modified afterward

Lambdas can access only final or effectively final local variables.

---

### 3️⃣ Can lambda access instance variables?

Yes.

Lambdas can access:

* Instance variables
* Static variables
* Final or effectively final local variables

Unlike local variables, instance variables do not need to be final.

---

### 4️⃣ Difference between lambda and anonymous class?

Lambda:

* Concise syntax
* Does not create new scope
* `this` refers to enclosing class
* Cannot define additional methods

Anonymous class:

* More verbose
* Creates new scope
* `this` refers to anonymous class
* Can define additional methods

---

### 5️⃣ What does `this` refer to inside lambda?

Inside a lambda, `this` refers to the enclosing class instance.

It does not refer to a new object like in anonymous classes.

---

# 🔹 1–2 YOE

---

### 1️⃣ Why must local variables be effectively final?

Because lambdas capture local variables from the enclosing scope.

If modification were allowed, it could lead to inconsistent state and concurrency issues.

The effectively final rule ensures safe variable capture.

---

### 2️⃣ Does lambda create a new scope?

No.

Lambda does not create a new scope.

You cannot redeclare a local variable inside lambda if it exists outside.

Anonymous classes create a new scope. Lambdas do not.

---

### 3️⃣ What are method references?

Method references are a shorthand notation for lambda expressions that call an existing method.

They improve readability when the lambda only forwards parameters.

Example:

```java
System.out::println
```

---

### 4️⃣ Types of method references?

1. Static method reference
   `Integer::parseInt`

2. Instance method reference (specific object)
   `System.out::println`

3. Arbitrary object method reference
   `String::toUpperCase`

4. Constructor reference
   `ArrayList::new`

---

### 5️⃣ When should you avoid lambda?

Avoid lambda when:

* Logic is complex and multi-line
* Readability decreases
* Multiple side effects exist
* Anonymous class is required (e.g., multiple methods)

Lambdas should be short and expressive.

---

# 🔹 2–3 YOE

---

### 1️⃣ How are lambdas implemented internally?

Lambdas are implemented using the `invokedynamic` instruction in the JVM.

At runtime, the JVM dynamically creates an implementation of the functional interface.

They are not traditional anonymous inner classes.

---

### 2️⃣ Is lambda compiled into anonymous class?

No.

Unlike anonymous classes, lambdas use `invokedynamic` and do not generate a separate `.class` file for each lambda.

They are more lightweight.

---

### 3️⃣ When would you prefer anonymous class over lambda?

Prefer anonymous class when:

* You need multiple methods
* You need to override default methods
* You need a new scope
* You need different `this` reference

Lambdas are only for single-method interfaces.

---

### 4️⃣ What are readability concerns with lambdas?

* Long multi-line lambdas reduce clarity
* Nested lambdas become hard to read
* Complex business logic inside lambda is bad practice

Best practice: Keep lambdas small and focused.

---

### 5️⃣ How do lambdas improve backend code?

They:

* Reduce boilerplate
* Simplify collection processing
* Improve readability in Streams
* Enable cleaner strategy pattern implementation
* Make asynchronous programming cleaner

They help write more declarative and expressive backend code.

---