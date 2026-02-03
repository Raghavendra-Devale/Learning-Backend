
# Lesson 14: Iterable, Iterator & Fail-Fast vs Fail-Safe

This note explains the difference between `Iterable` and `Iterator`, how iteration works internally in Java, and the concept of fail-fast and fail-safe iterators.

---

## 1. Iterable

`Iterable` represents a collection that can be iterated using a for-each loop.

### Key Point
- `Iterable` has only one method:

```java
Iterator<T> iterator();
````

Any class implementing `Iterable` can be used in a for-each loop.

---

## 2. Iterator

`Iterator` is responsible for **actual traversal** of elements.

### Important Methods

* `hasNext()`
* `next()`
* `remove()`

`remove()` is the **only safe way** to remove elements during iteration.

---

## 3. for-each Loop Internals

```java
for (Integer x : list) { }
```

Internally translates to:

```java
Iterator<Integer> it = list.iterator();
while (it.hasNext()) {
    Integer x = it.next();
}
```

---

## 4. Fail-Fast Iterators

Fail-fast iterators throw `ConcurrentModificationException` if the collection is structurally modified during iteration.

### Structural Modifications

* add()
* remove()
* clear()

Fail-fast behavior helps detect bugs early.

Examples:

* ArrayList
* HashMap
* HashSet

---

## 5. Fail-Safe Iterators

Fail-safe iterators do **not throw exceptions** during concurrent modification.

They work by:

* Iterating over a snapshot
* Or using weakly consistent views

Examples:

* ConcurrentHashMap
* CopyOnWriteArrayList

---

## 6. Fail-Fast vs Fail-Safe

| Aspect        | Fail-Fast | Fail-Safe |
| ------------- | --------- | --------- |
| Exception     | Yes       | No        |
| Consistency   | Strong    | Weak      |
| Memory        | Low       | Higher    |
| Bug detection | Immediate | Delayed   |

---

## 7. Backend Relevance

* Fail-fast iterators prevent silent data corruption
* Fail-safe iterators trade consistency for concurrency
* Choice depends on correctness vs performance needs

---

---

## 🧠 FINAL LOCKED MENTAL MODEL (REMEMBER THIS)

* for-each → uses **Iterator**
* Default iterators → **fail-fast**
* Safe removal → **Iterator.remove()**
* Fail-fast → detects bugs early
* Fail-safe → avoids exception but may be inconsistent

You’re now **interview-safe** on this topic.

---


