
# Lesson 8: equals() & hashCode()

This note explains the purpose, contract, and real-world importance of `equals()` and `hashCode()` in Java, especially in the context of collections and backend systems.

---

## 1. Equality in Java

Java supports two types of equality:

### Reference Equality (`==`)
- Checks if two references point to the same object

### Logical Equality (`equals()`)
- Checks if two objects are logically equal
- Default implementation in `Object` behaves like `==`

---

## 2. Why Override equals()

In backend systems, different objects may represent the same logical entity.

Example:
- Two `User` objects with the same `id`

Logical equality must be explicitly defined by overriding `equals()`.

---

## 3. equals() Contract

When overriding `equals()`, the following rules must be followed:

1. Reflexive: `x.equals(x)` is true
2. Symmetric: `x.equals(y)` equals `y.equals(x)`
3. Transitive: if `x.equals(y)` and `y.equals(z)`, then `x.equals(z)`
4. Consistent: result does not change unless state changes
5. Non-null: `x.equals(null)` is false

Breaking this contract leads to unpredictable behavior in collections.

---

## 4. What is hashCode()?

- Returns an integer value
- Used by hash-based collections like `HashMap` and `HashSet`
- Determines the bucket location for an object

---

## 5. hashCode() Contract (VERY IMPORTANT)

> If two objects are equal according to `equals()`, they must return the same `hashCode()`.

The reverse is not required.

---

## 6. How HashMap Uses equals() and hashCode()

1. `hashCode()` is used to locate the bucket
2. `equals()` is used to find the exact key within the bucket

Both are required for correct behavior.

---

## 7. Hash Collisions

- Two unequal objects can have the same `hashCode()`
- This is called a collision
- HashMap resolves collisions using `equals()`

Collisions are normal and expected.

---

## 8. Correct Implementation Pattern

```java
@Override
public boolean equals(Object o) {
    if (this == o) return true;
    if (o == null || getClass() != o.getClass()) return false;
    User user = (User) o;
    return id == user.id;
}

@Override
public int hashCode() {
    return Objects.hash(id);
}
````

---

## 9. Immutable Fields Rule

Fields used in `equals()` and `hashCode()` should be immutable.

Changing such fields after insertion into a hash-based collection can make the object unreachable.

---

## 10. Backend Relevance

* HashMap keys
* HashSet uniqueness
* Caching
* Hibernate entities
* Deduplication logic

Incorrect implementation leads to silent production bugs.
