# Functional Interfaces — Twisted Questions

---

### 1️⃣ Is this a functional interface?

```java
interface Test {
    void m1();
    void m2();
}
```

**Answer:**
No.

**Why?**

A functional interface must have exactly one abstract method.

Here, `m1()` and `m2()` are both abstract methods, so it violates the Single Abstract Method (SAM) rule.

---

### 2️⃣ Is this valid?

```java
interface Test {
    void m1();
    default void m2() {}
}
```

**Answer:**
Yes.

**Why?**

Only `m1()` is abstract.
`m2()` is a default method, and default methods do not count toward the abstract method count.

So this is a valid functional interface.

---

### 3️⃣ Why does this fail?

```java
int x = 10;
x = 20;
Runnable r = () -> System.out.println(x);
```

**Answer:**
`x` is not effectively final.

**Why?**

Local variables used inside a lambda must be final or effectively final.

Since `x` is reassigned, it is no longer effectively final, and compilation fails.

---

### 4️⃣ What does `this` refer to inside lambda?

**Answer:**
It refers to the enclosing class instance.

**Explanation:**

Lambdas do not create a new object context like anonymous classes.
Therefore, `this` refers to the outer class, not a new lambda instance.

---

### 5️⃣ Does lambda create a new scope?

**Answer:**
No.

**Explanation:**

Lambdas do not introduce a new scope.

You cannot redeclare a local variable inside a lambda if it already exists in the enclosing method.

Anonymous classes create a new scope; lambdas do not.

---