
# Lesson 12: Set Implementations in Java

This note explains Java `Set` implementations — `HashSet`, `LinkedHashSet`, and `TreeSet` — along with ordering concepts using `Comparable` and `Comparator`.  
This is a high-value interview topic tightly coupled with `equals()`, `hashCode()`, and collections internals.

---

## 1. What Is a Set?

A `Set` is a collection that:
- Does NOT allow duplicate elements
- Does NOT support index-based access
- Determines uniqueness based on implementation logic

Duplicate detection depends on:
- `equals()` and `hashCode()` (Hash-based sets)
- `compareTo()` / `Comparator` (TreeSet)

---

## 2. HashSet

### Internal Working
- `HashSet` is backed by a `HashMap`
- Elements are stored as **keys**
- A dummy constant object is used as value

```java
HashSet<E> → HashMap<E, Object>
````

### Duplicate Detection

1. `hashCode()` is called
2. Bucket is identified
3. `equals()` is used to check equality

### Properties

* No ordering guarantee
* Allows one `null`
* Average time complexity: **O(1)**

### Usage

* Fast deduplication
* Filtering unique elements
* Most commonly used Set

---

## 3. LinkedHashSet

### Internal Working

* Backed by `HashMap`
* Maintains a **doubly linked list** for order

### Properties

* Maintains **insertion order**
* Slightly more memory than HashSet
* Time complexity close to HashSet

### Usage

* When uniqueness + predictable iteration order is required
* API responses
* Logs
* Deterministic output

---

## 4. TreeSet

### Internal Working

* Backed by a **Red-Black Tree**
* Elements are stored in **sorted order**

### Ordering Is Based On

* `Comparable` (natural ordering)
* OR `Comparator` (custom ordering)

### Duplicate Detection ⚠️

TreeSet does NOT use `equals()`.

Duplicates are detected using:

```text
compareTo() == 0 OR comparator.compare() == 0
```

If comparison returns 0 → element is considered duplicate.

### Properties

* Sorted order
* No `null` (except legacy cases)
* Time complexity: **O(log n)**

### Usage

* Sorted data
* Range queries
* Ordered processing

---

## 5. Comparable — Natural Ordering

### What It Means

* Class defines its own ordering
* Only ONE natural order is possible

```java
class User implements Comparable<User> {
    int id;

    @Override
    public int compareTo(User other) {
        return this.id - other.id;
    }
}
```

### Used By

* TreeSet
* TreeMap
* Collections.sort()

---

## 6. Comparator — Custom Ordering

### What It Means

* Ordering logic is external to the class
* Multiple sorting strategies possible

```java
Comparator<User> byName =
    (u1, u2) -> u1.name.compareTo(u2.name);
```

### Advantages

* No need to modify class
* Multiple orderings supported
* Preferred in real backend systems

---

## 7. Comparable vs Comparator (Interview Table)

| Aspect             | Comparable   | Comparator              |
| ------------------ | ------------ | ----------------------- |
| Defined in         | Class itself | Separate class / lambda |
| Method             | compareTo()  | compare()               |
| Natural order      | Yes          | No                      |
| Multiple orderings | No           | Yes                     |
| Used by default    | Yes          | Only if provided        |

---

## 8. Important Interview Traps ⚠️

❌ HashSet maintains order
❌ TreeSet uses equals() for duplicates
❌ Comparator is slower than Comparable
❌ compareTo must return only -1, 0, 1
❌ All Sets allow null

---

## 9. Backend Usage Summary

* Deduplication → `HashSet`
* Ordered response → `LinkedHashSet`
* Sorted data → `TreeSet`
* Multiple sorting rules → `Comparator`

---

## 10. Interview-Safe Summary

> “HashSet provides fast, unordered uniqueness using hashing. LinkedHashSet preserves insertion order with slight overhead. TreeSet maintains sorted order using comparison logic and detects duplicates based on comparison results, not equals.”

---
