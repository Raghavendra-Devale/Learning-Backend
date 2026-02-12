# Optional — Twisted / Trap Questions

---

### 1️⃣ What is wrong here?

```java
Optional<User> user = Optional.of(null);
```

**Answer:**
Throws `NullPointerException`.

**Why?**

`Optional.of()` does not allow null values.
It expects a guaranteed non-null reference.

Correct approach:

```java
Optional<User> user = Optional.ofNullable(null);
```

Use `ofNullable()` when the value may be null.

---

### 2️⃣ Why is this inefficient?

```java
user.orElse(new User());
```

**Answer:**
`new User()` is created even if the Optional contains a value.

**Why?**

`orElse()` eagerly evaluates its argument.
The default object is created regardless of whether it is needed.

Better approach:

```java
user.orElseGet(User::new);
```

`orElseGet()` lazily creates the object only if the Optional is empty.

---

### 3️⃣ Why is this bad practice?

```java
class User {
    Optional<String> name;
}
```

**Answer:**
Optional should not be used as a class field.

**Why?**

* Optional is designed for return types.
* It complicates serialization (e.g., JSON).
* JPA/Hibernate does not handle Optional fields properly.
* It adds unnecessary wrapping inside domain models.

Fields should use normal types and allow null if necessary.

---

### 4️⃣ What happens?

```java
Optional<String> name = Optional.empty();
name.get();
```

**Answer:**
Throws `NoSuchElementException`.

**Why?**

`get()` assumes a value is present.
Calling it on an empty Optional defeats the purpose of Optional.

Safer alternatives:

* `orElse()`
* `orElseThrow()`
* `ifPresent()`

---

### 5️⃣ Why use flatMap instead of map sometimes?

**Answer:**
To avoid nested `Optional<Optional<T>>`.

**Explanation:**

If the mapping function already returns an Optional:

```java
Optional<Optional<String>>
```

This creates nesting.

Using `flatMap()` flattens it into:

```java
Optional<String>
```

Use `flatMap()` when your mapping function returns Optional.

---