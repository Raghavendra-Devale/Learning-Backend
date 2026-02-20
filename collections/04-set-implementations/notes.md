

# Lesson 12 — Java Set Implementations (Interview + Real Understanding)


## 1. What a Set *Really* Guarantees

A `Set` guarantees **uniqueness**, but here’s the important nuance:

> A Set does NOT define *how* uniqueness is checked — the implementation does.

Different Sets answer the question:

> “When are two elements considered the same?”

in completely different ways.

| Set Type      | How duplicates are detected  |
| ------------- | ---------------------------- |
| HashSet       | `hashCode()` + `equals()`    |
| LinkedHashSet | Same as HashSet              |
| TreeSet       | `compareTo()` / `Comparator` |

This distinction causes many interview mistakes.

---

## 2. HashSet — Fast Uniqueness via Hashing

### Internal Reality

`HashSet` is basically a thin wrapper around `HashMap`.

Internally:

```text
HashSet<E> → HashMap<E, PRESENT>
```

The element becomes the **key**, and a dummy object is stored as value.

So all HashMap rules apply.

---

### How Duplicate Detection Works

1. Call `hashCode()`
2. Find bucket
3. Use `equals()` to confirm equality

Important insight:

Two objects with same hashCode can still coexist if `equals()` returns false.

---

### Properties

* No ordering guarantee
* Allows one `null`
* Average operations → **O(1)**

---

### Real Backend Usage

* Removing duplicates from lists
* Membership checks
* Fast lookup filters

If you see “unique + fast”, think HashSet first.

---

## 3. LinkedHashSet — Order + Hashing

LinkedHashSet answers a common problem:

> “I want uniqueness, but iteration order must be predictable.”

---

### Internal Design

It extends HashSet behavior but adds:

* a **doubly linked list** connecting entries in insertion order.

So internally you get:

```text
Hash table + linked ordering
```

---

### Properties

* Maintains insertion order
* Slightly higher memory usage
* Nearly same performance as HashSet

---

### Why This Exists

HashSet iteration order can change after resize.

LinkedHashSet guarantees deterministic output — extremely useful for:

* API responses
* logging
* consistent testing results

Backend engineers often prefer predictable iteration.

---

## 4. TreeSet — Sorted Set (Completely Different Beast)

TreeSet is NOT hash-based.

It uses a **Red-Black Tree** (self-balancing binary search tree).

Meaning:

* elements always remain sorted
* operations cost **O(log n)**

---

### Ordering Mechanism

TreeSet must compare elements to decide placement.

It uses either:

* `Comparable` (natural ordering)
* `Comparator` (custom ordering)

---

### ⚠️ Critical Interview Concept — Duplicate Detection

TreeSet does NOT use `equals()`.

Instead:

```text
compareTo() == 0
OR
comparator.compare() == 0
```

means duplicate.

This surprises many developers.

Example:

Two objects unequal by `equals()` but returning `0` in comparison → TreeSet keeps only one.

---

### Properties

* Sorted iteration
* No null elements (comparison impossible)
* O(log n) operations

---

### Real Uses

* ranking systems
* sorted reports
* range queries
* leaderboards

---

## 5. Comparable — Natural Ordering

Comparable defines ordering **inside the class itself**.

Example:

```java
class User implements Comparable<User> {
    int id;

    public int compareTo(User other) {
        return Integer.compare(this.id, other.id);
    }
}
```

Meaning:

> Objects know how to compare themselves.

---

### Limitation

Only ONE natural ordering allowed.

That becomes restrictive quickly.

---

## 6. Comparator — External Ordering (Industry Favorite)

Comparator moves comparison logic outside the class.

Example:

```java
Comparator<User> byName =
    (u1, u2) -> u1.name.compareTo(u2.name);
```

Now you can create:

* sort by name
* sort by age
* sort by salary

without modifying the class.

---

### Why Backend Systems Prefer Comparator

Domain models should not hardcode sorting logic.

Comparator keeps models clean and flexible.

This aligns with separation of concerns.

---

## 7. Comparable vs Comparator — Real Interpretation

| Concept             | Comparable    | Comparator        |
| ------------------- | ------------- | ----------------- |
| Who owns logic      | Object itself | External strategy |
| Flexibility         | Low           | High              |
| Number of orderings | One           | Many              |
| Real-world usage    | Limited       | Very common       |

Modern Java (lambdas + streams) heavily favors Comparator.

---

## 8. Expanded Interview Traps (Important)

### ❌ “TreeSet uses equals()”

No — comparison defines equality.

---

### ❌ “Comparator is slower”

Negligible difference. Algorithm dominates runtime.

---

### ❌ “compareTo must return -1, 0, 1”

Any negative or positive integer works.

Correct:

```java
return this.age - other.age; // valid
```

---

### ❌ “All Sets allow null”

Only hash-based sets do.

TreeSet usually throws `NullPointerException`.

---

## 9. Backend Decision Guide (Practical Thinking)

| Requirement              | Best Choice   |
| ------------------------ | ------------- |
| Fast uniqueness          | HashSet       |
| Unique + insertion order | LinkedHashSet |
| Unique + sorted          | TreeSet       |
| Multiple sorting rules   | Comparator    |

---

## 🧠 One Strong Interview Explanation

> HashSet provides fast uniqueness using hashing, LinkedHashSet maintains insertion order using a linked structure on top of hashing, and TreeSet maintains sorted order using a red-black tree where duplicates are determined by comparison rather than equals.

---

## The Deeper Engineering Insight

Sets reveal an important truth about software design:

“Equality” is not universal — it depends on context.

HashSet asks: *Are these objects logically equal?*
TreeSet asks: *Do these objects occupy the same position in an ordering?*

Two different philosophical questions, two different data structures.

This idea shows up everywhere later — database indexing, caching keys, stream grouping, even distributed systems hashing.

