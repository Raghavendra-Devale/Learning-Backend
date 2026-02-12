# Lambda Expressions — Twisted / Trap Questions

---

### 1️⃣ Why does this fail?

```java
int x = 10;
x = 20;
Runnable r = () -> System.out.println(x);
```

**Answer:**
`x` is not effectively final.

**Why?**

Local variables captured inside a lambda must be final or effectively final.
Since `x` is reassigned (`x = 20`), it is no longer effectively final.

The compiler prevents this to ensure safe variable capture.

---

### 2️⃣ Does lambda create a new scope?

**Answer:**
No.

**Explanation:**

Lambdas do not introduce a new scope.
You cannot redeclare a local variable inside a lambda if it exists in the enclosing scope.

This differs from anonymous classes, which create a new scope.

---

### 3️⃣ What does `this` refer to inside lambda?

**Answer:**
The enclosing class instance.

**Explanation:**

Inside a lambda, `this` refers to the outer class object.
It does not refer to a new object like in an anonymous class.

This is a key behavioral difference.

---

### 4️⃣ Can lambda have multiple statements?

**Answer:**
Yes.

**Explanation:**

If multiple statements are used, braces `{}` are required.

Example:

```java
(a, b) -> {
    int sum = a + b;
    return sum;
}
```

If the functional interface method has a return type, a `return` statement is mandatory when using braces.

---

### 5️⃣ Is this valid?

```java
Comparator<Integer> c = (a, b) -> {
    System.out.println(a);
};
```

**Answer:**
No.

**Why?**

The `Comparator` interface method `compare(T o1, T o2)` must return an `int`.

This lambda does not return a value, so compilation fails.

Correct version:

```java
Comparator<Integer> c = (a, b) -> {
    System.out.println(a);
    return Integer.compare(a, b);
};
```

---

### 6️⃣ Is lambda compiled to anonymous class?

**Answer:**
No.

**Explanation:**

Lambdas are implemented using the `invokedynamic` instruction in the JVM.

They do not generate a separate anonymous inner class file.
They are more lightweight and optimized at runtime.

---