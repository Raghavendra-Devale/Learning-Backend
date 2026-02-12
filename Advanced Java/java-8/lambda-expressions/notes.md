# Lambda Expressions — Complete Notes

---

# 1. What is a Lambda Expression?

A lambda expression is a concise way to represent an anonymous function in Java.

It provides the implementation of a **functional interface’s single abstract method (SAM)**.

Introduced in Java 8, lambdas enable functional programming style in Java.

---

## Key Characteristics

* Anonymous (no name)
* No explicit return type required
* Used only with functional interfaces
* Enables declarative programming
* Often used with Streams and Collections

---

## Basic Syntax

```java
(parameters) -> expression
(parameters) -> { statements }
```

---

# 2. Lambda Syntax Variations

---

### 1️⃣ With Explicit Types

```java
(int a, int b) -> a + b
```

Used when type inference is unclear.

---

### 2️⃣ With Type Inference

```java
(a, b) -> a + b
```

Most common usage. Compiler infers types.

---

### 3️⃣ Single Parameter (No Parentheses Required)

```java
x -> x * 2
```

Parentheses optional when there is exactly one parameter.

---

### 4️⃣ Multiple Statements (Block Body)

```java
(a, b) -> {
    int sum = a + b;
    return sum;
}
```

Important rule:

If braces `{}` are used, `return` is mandatory.

If single expression is used, return is implicit.

---

# 3. Functional Interface Requirement

A lambda can only be used where a functional interface is expected.

---

## What is a Functional Interface?

An interface with exactly one abstract method.

Example:

```java
@FunctionalInterface
interface Calculator {
    int add(int a, int b);
}
```

Usage:

```java
Calculator add = (a, b) -> a + b;
```

---

## Common Built-in Functional Interfaces

* Predicate<T>
* Function<T, R>
* Consumer<T>
* Supplier<T>
* Comparator<T>

These are heavily used in backend development.

---

# 4. Effectively Final Rule

Local variables used inside a lambda must be:

* final
  OR
* effectively final

Effectively final means the variable is assigned once and not modified.

Example:

```java
int x = 10;
Function<Integer, Integer> f = n -> n + x;
```

Valid because `x` is not modified.

---

## Why This Rule Exists?

Because lambdas capture variables from enclosing scope.
Allowing modification could lead to inconsistent state.

This ensures safe variable capture.

---

# 5. Scope Rules

Lambda does not create a new scope.

Example:

```java
int x = 10;

list.forEach(n -> {
    int x = 20; // Compilation error
});
```

You cannot redeclare a local variable inside a lambda if it exists outside.

---

## Important Difference

Anonymous classes create a new scope.
Lambdas do not.

---

# 6. `this` Keyword Behavior

---

### In Anonymous Class

`this` refers to the anonymous class instance.

---

### In Lambda

`this` refers to the enclosing class instance.

Example:

```java
public class Example {
    void test() {
        Runnable r = () -> {
            System.out.println(this);
        };
    }
}
```

Here, `this` refers to `Example` object.

This is a common interview difference.

---

# 7. Method References

Method references provide a cleaner alternative to lambda expressions when the lambda only calls an existing method.

---

## Types of Method References

---

### 1️⃣ Static Method Reference

```java
Integer::parseInt
```

Equivalent to:

```java
s -> Integer.parseInt(s)
```

---

### 2️⃣ Instance Method Reference (Specific Object)

```java
System.out::println
```

Equivalent to:

```java
x -> System.out.println(x)
```

---

### 3️⃣ Arbitrary Object Method Reference

```java
String::toUpperCase
```

Equivalent to:

```java
s -> s.toUpperCase()
```

---

### 4️⃣ Constructor Reference

```java
ArrayList::new
```

Equivalent to:

```java
() -> new ArrayList<>()
```

Method references improve readability.

---

# 8. Lambda vs Anonymous Class

---

## Anonymous Class

* Verbose
* Creates separate class
* Has its own scope
* `this` refers to anonymous class
* Can define additional methods

---

## Lambda

* Concise
* No new scope
* `this` refers to enclosing class
* Cleaner and more readable
* Cannot define extra methods

---

## Key Interview Difference

Lambda is not just syntactic sugar.
It behaves differently regarding scope and `this`.

---

# 9. Backend Usage

Lambdas are widely used in backend development.

---

## Common Usage Areas

* Stream API
* Sorting with Comparator
* Callback implementations
* Strategy pattern
* Event handling
* Asynchronous tasks
* CompletableFuture

---

## Example — Sorting

```java
users.sort(Comparator.comparing(User::getAge));
```

---

## Example — Filtering

```java
users.stream()
     .filter(user -> user.isActive())
     .toList();
```

---

## Example — Strategy Pattern

```java
public void process(PaymentStrategy strategy) {
    strategy.pay();
}
```

Lambda implementation:

```java
process(() -> System.out.println("Processing payment"));
```

---

# 10. Common Mistakes

---

❌ Modifying captured variable

❌ Writing very long lambdas (hurts readability)

❌ Not understanding scope rules

❌ Confusing lambda with anonymous class behavior

❌ Using lambda where method reference is clearer

---

# 11. Best Practices (Backend Focus)

* Keep lambdas short and readable.
* Prefer method references when possible.
* Avoid side effects inside lambdas.
* Do not put complex business logic inside lambda.
* Use meaningful parameter names.
* Understand functional interfaces clearly.

---