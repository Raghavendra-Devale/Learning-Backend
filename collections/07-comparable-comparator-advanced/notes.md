
# Lesson 15: Comparable vs Comparator (Advanced)

This note covers advanced concepts, consistency rules, and real interview traps related to `Comparable` and `Comparator`, especially with sorted collections like TreeSet and TreeMap.

---

## 1. Core Rule (Very Important)

Comparison logic must be **consistent with equals**.

Rule:
```

if a.equals(b) == true
then compare(a, b) must return 0

````

Failing this rule can cause silent data loss in sorted collections.

---

## 2. Why TreeSet Can Drop Elements

TreeSet determines uniqueness using:
- compareTo() or Comparator.compare()

If comparison returns 0:
- Element is treated as duplicate
- New element is ignored

This happens even if equals() returns false.

---

## 3. Comparable vs Comparator (Advanced View)

### Comparable
- Defines **natural ordering**
- Only one ordering allowed
- Becomes part of class contract
- Hard to change later

Use only when there is one obvious ordering (e.g., ID, timestamp).

---

### Comparator
- Defines **external ordering**
- Multiple sorting strategies possible
- No class modification required
- Preferred in backend systems

---

## 4. Subtraction-Based Comparison Trap

❌ Unsafe:
```java
return a - b;
````

Problems:

* Integer overflow
* Incorrect ordering

✅ Safe:

```java
return Integer.compare(a, b);
```

---

## 5. Comparator Chaining (Java 8+)

```java
Comparator<User> cmp =
    Comparator.comparing(User::getAge)
              .thenComparing(User::getName);
```

Benefits:

* Readable
* Overflow-safe
* Stable ordering

---

## 6. Null Handling in Comparators

By default:

* compareTo() throws NullPointerException

Safe handling:

```java
Comparator<User> cmp =
    Comparator.nullsLast(
        Comparator.comparing(User::getName)
    );
```

---

## 7. TreeSet Ordering Limitation

* Comparator is fixed at TreeSet creation
* Ordering cannot be changed later
* For multiple orderings, use List + sort()

---

## 8. Backend Impact

* Incorrect comparison → silent bugs
* TreeSet / TreeMap heavily rely on comparison
* Comparator preferred for evolving systems

---

---

## 🧠 LOCK THIS CORE IDEA (IMPORTANT)

* Hash-based collections → `equals + hashCode`
* Sorted collections → **comparison logic**
* `compare() == 0` → duplicate
* Wrong comparison → **silent data loss**

You’re now aligned.

---
