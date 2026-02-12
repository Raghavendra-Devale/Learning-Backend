# Functional Interfaces — Complete Notes

---

# 1. What is a Functional Interface?

A functional interface is an interface that contains **exactly one abstract method** (Single Abstract Method — SAM).

It may contain:

* Multiple default methods
* Multiple static methods
* Methods from `Object` class (equals, hashCode, toString)

But only **one abstract method** is allowed.

---

## Example

```java
@FunctionalInterface
interface Calculator {
    int calculate(int a, int b);
}
```

Here, `calculate()` is the single abstract method.

---

# 2. Why Functional Interfaces Exist

Functional interfaces were introduced in Java 8 to support **Lambda Expressions**.

A lambda expression provides the implementation of the single abstract method of a functional interface.

Example:

```java
Calculator add = (a, b) -> a + b;
```

Here, the lambda implements the `calculate()` method.

Without functional interfaces, lambdas cannot exist.

---

# 3. @FunctionalInterface Annotation

This annotation is optional but highly recommended.

It ensures:

* The interface has exactly one abstract method
* Compiler error occurs if another abstract method is added

Example:

```java
@FunctionalInterface
interface Task {
    void execute();
}
```

If another abstract method is added, compilation fails.

---

# 4. Built-in Functional Interfaces (java.util.function)

Java provides several commonly used functional interfaces.

---

## Predicate<T>

Represents a boolean-valued function.

Input → boolean

Commonly used in:

* `filter()` in Streams

Example:

```java
Predicate<User> isAdult = u -> u.getAge() >= 18;
```

---

## Function<T, R>

Represents a function that takes one argument and produces a result.

Input → Output

Commonly used in:

* `map()` in Streams

Example:

```java
Function<User, String> getName = User::getName;
```

---

## Consumer<T>

Represents an operation that takes a single input and returns no result.

Input → void

Commonly used in:

* `forEach()`

Example:

```java
Consumer<User> printer = System.out::println;
```

---

## Supplier<T>

Represents a supplier of results.

No input → Output

Example:

```java
Supplier<UUID> supplier = () -> UUID.randomUUID();
```

---

## BiFunction<T, U, R>

Represents a function that takes two arguments and produces a result.

Two inputs → Output

Example:

```java
BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;
```

---

# 5. Anonymous Class vs Lambda

---

## Anonymous Class (Before Java 8)

```java
Runnable r = new Runnable() {
    @Override
    public void run() {
        System.out.println("Running");
    }
};
```

Characteristics:

* Creates a separate class
* Has its own scope
* Can shadow variables
* Verbose syntax

---

## Lambda

```java
Runnable r = () -> System.out.println("Running");
```

Characteristics:

* Concise
* No new scope
* Cannot shadow local variables
* Cleaner syntax

---

# 6. Key Differences

---

### 1️⃣ `this` Reference

* Anonymous class → refers to anonymous class instance
* Lambda → refers to enclosing class instance

---

### 2️⃣ Scope

* Anonymous class → creates new scope
* Lambda → does not create new scope

---

### 3️⃣ Verbosity

* Anonymous class → verbose
* Lambda → concise

---

### 4️⃣ Implementation

* Anonymous class → compiled as separate inner class
* Lambda → implemented using `invokedynamic` (JVM optimized)

---

# 7. Effectively Final Rule

Lambdas can access only:

* final variables
  OR
* effectively final variables

Example:

```java
int x = 10;
Runnable r = () -> System.out.println(x);
```

Valid because `x` is not modified.

If `x` is modified later:

```java
x = 20;
```

Compilation fails.

---

## Why This Rule Exists

To ensure safe variable capture and prevent inconsistent state, especially in concurrent environments.

---

# 8. Backend Relevance

Functional interfaces enable modern backend programming patterns such as:

* Stream processing
* Asynchronous execution
* Callback handling
* Strategy pattern implementation
* Event-driven programming

Example — Strategy Pattern:

```java
public void process(PaymentStrategy strategy) {
    strategy.pay();
}
```

Lambda usage:

```java
process(() -> System.out.println("Processing payment"));
```

---

# 9. Best Practices

* Use built-in functional interfaces when possible.
* Keep lambdas short and readable.
* Avoid complex business logic inside lambdas.
* Use `@FunctionalInterface` annotation for clarity.
* Understand scope and `this` behavior clearly.

---