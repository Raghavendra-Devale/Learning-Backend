# Optional — Complete Notes 

---

# 1. What is Optional?

`Optional` is a container object that may or may not contain a non-null value.

It was introduced in Java 8 to model the **explicit absence of a value** instead of returning `null`.

### Purpose

* Avoid `NullPointerException`
* Make absence explicit in API contracts
* Encourage safer handling of nullable values
* Improve readability in method return types

---

# 2. Why Optional Was Introduced

Before Java 8:

```java
User user = repository.findById(id);
if (user != null) {
    System.out.println(user.getEmail());
}
```

Problem:

* Easy to forget null checks
* Leads to NullPointerException
* Makes API contracts unclear

With Optional:

```java
Optional<User> user = repository.findById(id);
user.ifPresent(u -> System.out.println(u.getEmail()));
```

Now absence is explicitly handled.

---

# 3. Creating Optional

---

### Optional.of(value)

```java
Optional<User> optional = Optional.of(user);
```

* Throws `NullPointerException` if value is null.
* Use only when you are sure value is non-null.

---

### Optional.ofNullable(value)

```java
Optional<User> optional = Optional.ofNullable(user);
```

* Safe creation.
* Returns empty Optional if value is null.
* Most commonly used.

---

### Optional.empty()

```java
Optional<User> optional = Optional.empty();
```

* Creates an empty Optional explicitly.

---

# 4. Checking & Accessing Values

---

### get()

```java
optional.get();
```

* Returns value if present.
* Throws `NoSuchElementException` if empty.
* Not recommended without checking.

---

### isPresent()

```java
if (optional.isPresent()) {
    User user = optional.get();
}
```

* Checks whether value exists.
* Works but considered less modern style.

---

### ifPresent()

```java
optional.ifPresent(user -> System.out.println(user.getEmail()));
```

* Executes action only if value is present.
* Cleaner than `isPresent()` + `get()`.

---

# 5. Default Value Handling

---

### orElse(defaultValue)

```java
User user = optional.orElse(defaultUser);
```

* Returns value if present.
* Otherwise returns defaultValue.
* Important: defaultValue is always evaluated.

---

### orElseGet(supplier)

```java
User user = optional.orElseGet(() -> createDefaultUser());
```

* Supplier executes only if Optional is empty.
* More efficient when default creation is expensive.

---

### orElseThrow()

```java
User user = optional.orElseThrow();
```

* Throws `NoSuchElementException` if empty.

Custom exception:

```java
User user = optional.orElseThrow(() -> new RuntimeException("User not found"));
```

---

# 6. Transformations

Optional supports functional-style transformations.

---

### map()

Transforms the contained value if present.

```java
Optional<String> email =
    optionalUser.map(User::getEmail);
```

If user exists → returns Optional<String>
If empty → remains empty

---

### flatMap()

Used when mapping function already returns Optional.

Avoids nested Optional.

Wrong:

```java
Optional<Optional<String>>
```

Correct:

```java
optionalUser.flatMap(user -> repository.findEmail(user.getId()));
```

---

# 7. Chaining Example

Safe chaining without null checks:

```java
String email =
    Optional.ofNullable(user)
            .map(User::getAddress)
            .map(Address::getEmail)
            .orElse("Not Available");
```

This avoids multiple null checks.

---

# 8. Backend Usage

Common real-world usage:

✔ Repository return types (e.g., findById)
✔ Null-safe value transformation
✔ Optional chaining
✔ Returning explicit absence from service methods

Example:

```java
public Optional<User> findByEmail(String email);
```

---

# 9. Common Anti-Patterns

---

❌ Using Optional as a class field

```java
class User {
    Optional<String> email; // Not recommended
}
```

---

❌ Using Optional in entity attributes (JPA entities)

JPA does not handle Optional fields well.

---

❌ Serializing Optional in DTO

DTOs should contain actual values, not Optional.

---

❌ Calling get() blindly

Always handle absence properly.

---

❌ Using Optional for every variable

Optional is mainly for method return types, not local variables everywhere.

---

# 10. Best Practices (Backend Focus)

* Use Optional for return types, not fields.
* Prefer `orElseGet()` over `orElse()` for expensive defaults.
* Avoid `isPresent()` + `get()` pattern.
* Do not return null instead of Optional.
* Never use Optional in setters.

---