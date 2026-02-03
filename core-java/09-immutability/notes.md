
# Lesson 17: Immutability & Defensive Copying

This note explains immutability in Java, why it matters in backend systems, and how defensive copying is used to create truly immutable classes.

---

## 1. What Is Immutability?

An immutable object is one whose **state cannot be changed after creation**.

Immutability means:
- No observable state change
- Safe to share between threads
- Predictable behavior

---

## 2. Why Immutability Matters

Immutability provides:
- Thread safety (no synchronization required)
- Security (prevents data tampering)
- Predictability and easier reasoning
- Safe usage as HashMap keys

Common immutable classes:
- String
- Integer
- LocalDate

---

## 3. `final` vs Immutability (Important)

`final`:
- Prevents reassignment of a reference

Immutability:
- Prevents state change of the object

```java
final List<String> list = new ArrayList<>();
list.add("A"); // allowed – object is mutable
````

`final` alone does NOT make an object immutable.

---

## 4. Rules to Create an Immutable Class

An immutable class should:

1. Be declared `final`
2. Have all fields `private final`
3. Provide no setters
4. Never expose internal mutable objects
5. Use defensive copying for mutable fields

Missing any rule breaks immutability.

---

## 5. Defensive Copying

Defensive copying means **returning a copy instead of the actual internal object**.

### Wrong (breaks immutability)

```java
public Date getDob() {
    return dob;
}
```

### Correct (defensive copy)

```java
public Date getDob() {
    return new Date(dob.getTime());
}
```

---

## 6. Defensive Copying in Constructor

```java
public User(Date dob) {
    this.dob = new Date(dob.getTime());
}
```

Reason:

* Caller may modify the original object after passing it to constructor

Immutable classes must defend:

* Inputs
* Outputs

---

## 7. Why String Is Immutable (Interview Favorite)

String is immutable because:

* It is used in security-sensitive operations
* It is widely shared across threads
* It is used as a HashMap key
* It enables string pooling for performance

---

## 8. Backend Usage of Immutability

Use immutable objects for:

* DTOs
* Configuration objects
* Cache keys
* Value objects
* Shared read-only data

Use mutable objects for:

* Entities
* Aggregates
* Business state changes

---

## 9. Interview-Safe Summary

> “Immutability prevents state changes after object creation, improving thread safety, security, and predictability. Defensive copying is required when immutable objects contain mutable fields.”

---

