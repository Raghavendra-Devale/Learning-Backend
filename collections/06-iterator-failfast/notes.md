

# Lesson 14: Iterable, Iterator & Fail-Fast vs Fail-Safe

This lesson explains how iteration works internally in Java collections, the difference between `Iterable` and `Iterator`, and how Java handles modification during traversal.



## 1. Concept Overview

Iteration in Java separates **data storage** from **data traversal**.

* A collection stores elements.
* An iterator controls how elements are accessed sequentially.

This design allows multiple independent traversals over the same collection and enables safe detection of modification errors.

---

## 2. Iterable

`Iterable` represents any object whose elements can be traversed one by one.

### Key Method

```java
Iterator<T> iterator();
```

Any class implementing `Iterable` can be used in a **for-each loop**.

Example:

```java
for (Integer x : list) {
    System.out.println(x);
}
```

The collection itself does not perform iteration; it only provides an iterator.

---

## 3. Iterator

`Iterator` performs the actual traversal of elements.

### Important Methods

```java
boolean hasNext();
T next();
void remove();
```

* `hasNext()` → checks if more elements exist
* `next()` → returns the next element
* `remove()` → safely removes the current element during iteration

### Why `Iterator.remove()` Is Safe

The iterator internally tracks collection modifications.
Using `iterator.remove()` keeps the iterator synchronized with the collection state.

Directly calling collection methods like `list.remove()` during iteration breaks this synchronization.

---

## 4. for-each Loop Internals

A for-each loop is syntactic sugar over an iterator.

```java
for (Integer x : list) { }
```

Internally becomes:

```java
Iterator<Integer> it = list.iterator();
while (it.hasNext()) {
    Integer x = it.next();
}
```

Because the iterator is hidden, you cannot directly call `remove()` inside a for-each loop.

---

## 5. Fail-Fast Iterators

Fail-fast iterators throw `ConcurrentModificationException` when a collection is structurally modified during iteration.

### Structural Modifications

* `add()`
* `remove()`
* `clear()`

Most collections maintain an internal modification counter.
If the iterator detects a mismatch between expected and actual modification counts, it immediately fails.

Examples:

* `ArrayList`
* `HashMap`
* `HashSet`

### Important Note

Fail-fast behavior is **best-effort bug detection**, not thread safety.
It helps identify programming errors early but does not guarantee detection in all concurrent scenarios.

---

## 6. Fail-Safe Iterators

Fail-safe iterators allow modification during iteration without throwing exceptions.

They achieve this by:

* Iterating over a snapshot copy, or
* Providing weakly consistent views of data

Examples:

* `CopyOnWriteArrayList`
* `ConcurrentHashMap`

### Characteristics

* No `ConcurrentModificationException`
* Iterator may not reflect latest updates
* Higher memory or processing cost

---

## 7. Fail-Fast vs Fail-Safe

| Aspect              | Fail-Fast | Fail-Safe |
| ------------------- | --------- | --------- |
| Exception           | Yes       | No        |
| Consistency         | Strong    | Weak      |
| Memory Usage        | Low       | Higher    |
| Concurrency Support | Limited   | High      |
| Bug Detection       | Immediate | Delayed   |

---

## 8. Safe Removal During Iteration

Incorrect:

```java
for (Integer x : list) {
    list.remove(x); // throws ConcurrentModificationException
}
```

Correct:

```java
Iterator<Integer> it = list.iterator();
while (it.hasNext()) {
    Integer val = it.next();
    if (val % 2 == 0) {
        it.remove();
    }
}
```

---

## 9. Backend Relevance

* Fail-fast iterators prevent silent logical errors.
* Fail-safe iterators prioritize concurrency and availability.
* Choosing between them depends on correctness vs performance needs.

Examples:

* Financial or transactional data → prefer fail-fast behavior.
* Highly concurrent read systems → prefer fail-safe collections.

---

## 🧠 Mental Model

* `Iterable` → provides an iterator
* `Iterator` → performs traversal
* for-each loop → internally uses iterator
* Default iterators → fail-fast
* Safe removal → `Iterator.remove()`
* Fail-fast → detects modification bugs early
* Fail-safe → allows concurrent modification with weaker consistency

---
