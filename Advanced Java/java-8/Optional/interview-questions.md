# Optional — Interview Questions

---

# 🔹 0 Level

---

### 1️⃣ What is Optional?

Optional is a container object that may or may not contain a non-null value.

It is used to represent the presence or absence of a value explicitly instead of returning null.

---

### 2️⃣ Why was it introduced?

Optional was introduced to:

* Reduce NullPointerException
* Make absence of value explicit
* Improve API design
* Encourage safer null handling

It forces developers to handle missing values consciously.

---

# 🔹 Fresher Level

---

### 1️⃣ Difference between of() and ofNullable()?

**Optional.of(value)**

* Throws NullPointerException if value is null.
* Use only when value is guaranteed non-null.

**Optional.ofNullable(value)**

* Returns empty Optional if value is null.
* Safe creation method.

---

### 2️⃣ Difference between orElse() and orElseGet()?

**orElse(defaultValue)**

* Always evaluates defaultValue, even if Optional contains a value.

**orElseGet(supplier)**

* Executes supplier only if Optional is empty.

Important in performance-sensitive code when default creation is expensive.

---

### 3️⃣ What happens if get() is called on empty Optional?

It throws `NoSuchElementException`.

That’s why calling `get()` without checking is discouraged.

---

### 4️⃣ What is Optional.empty()?

It returns an empty Optional instance that contains no value.

Used to explicitly represent absence.

---

# 🔹 1–2 YOE

---

### 1️⃣ When should Optional be used?

Optional should be used:

* As method return type
* When value may or may not be present
* In repository/service layer APIs

It makes the contract clear that result may be absent.

---

### 2️⃣ When should it NOT be used?

Optional should not be used:

* As class fields
* In entity attributes
* In DTO fields
* In method parameters
* For every local variable

It is mainly intended for return types.

---

### 3️⃣ Difference between map() and flatMap()?

**map()**
Transforms the value inside Optional.
Returns Optional of transformed type.

**flatMap()**
Used when mapping function already returns Optional.
Prevents nested Optional.

Example:

* map → Optional<String>
* flatMap → avoids Optional<Optional<String>>

---

### 4️⃣ Why is get() discouraged?

Because:

* It defeats the purpose of Optional
* Can throw NoSuchElementException
* Encourages unsafe access

Better alternatives:

* orElse
* orElseGet
* orElseThrow
* ifPresent

---

### 5️⃣ How does Optional improve code readability?

It:

* Makes absence explicit in method signatures
* Reduces nested null checks
* Encourages fluent and declarative handling
* Makes API contracts clearer

Example:

```java
Optional<User> findById(Long id);
```

Clearly indicates user may not exist.

---

# 🔹 2–3 YOE

---

### 1️⃣ Why should Optional not be used in entity fields?

Because:

* JPA does not handle Optional fields well
* It complicates serialization
* It is not meant for state representation
* Optional is designed for return types

Entities should use regular fields and null if necessary.

---

### 2️⃣ How would you chain Optional safely?

Example:

```java
String email =
    Optional.ofNullable(user)
            .map(User::getAddress)
            .map(Address::getEmail)
            .orElse("Not Available");
```

This avoids multiple null checks and safely handles absence.

---

### 3️⃣ Performance impact of Optional?

Optional introduces slight object creation overhead.

In most backend applications, impact is negligible.

However, in tight loops or performance-critical sections, it may add minor overhead.

It should not be overused in hot paths.

---

### 4️⃣ When is Optional unnecessary?

Optional is unnecessary:

* For private methods with controlled inputs
* When value is guaranteed non-null
* Inside local variables
* For simple internal null checks

It is mainly useful in public API boundaries.

---

### 5️⃣ How is Optional different from null check?

Null check:

* Manual
* Easy to forget
* Not part of method signature

Optional:

* Explicit in return type
* Forces caller to handle absence
* Encourages safer functional handling

Optional improves API design, not just null safety.

---