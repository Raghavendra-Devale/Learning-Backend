
# Lesson 16: Map Implementations in Java

This lesson explains the differences between `HashMap`, `LinkedHashMap`, and `TreeMap`, focusing on internal working, ordering behavior, performance characteristics, and backend use cases.


## 1. Map Basics

A `Map` stores key–value pairs where:

* Keys are unique
* Values may be duplicated

Key uniqueness and iteration order depend on the specific implementation.

A map primarily performs three operations:

* Insert (`put`)
* Retrieve (`get`)
* Remove (`remove`)

Performance and behavior vary based on how keys are stored internally.

---

## 2. HashMap

### Internal Working

`HashMap` is based on a **hash table**.

Steps during insertion:

1. `hashCode()` is calculated for the key
2. Hash determines bucket index
3. Keys in the same bucket are compared using `equals()`
4. Entry is stored in that bucket

From Java 8 onward:

* High-collision buckets are converted into **balanced trees** (Red-Black Trees) to improve performance.

---

### Properties

* No ordering guarantee
* Allows one `null` key
* Allows multiple `null` values
* Not thread-safe
* Average time complexity: **O(1)**
* Worst case (heavy collisions): **O(log n)** after treeification

---

### Backend Usage

* Fast lookups
* Caching layers
* Session or configuration storage
* General-purpose key–value storage

`HashMap` is the default choice when ordering is not required.

---

## 3. LinkedHashMap

### Internal Working

`LinkedHashMap` extends `HashMap` by maintaining a **doubly linked list** connecting entries.

This list preserves iteration order while retaining hash-based lookup performance.

---

### Ordering Modes

1. **Insertion Order** (default)
   Elements iterate in the order they were added.

2. **Access Order** (optional)
   Recently accessed entries move to the end.

Example:

```java id="k3f9lp"
new LinkedHashMap<>(16, 0.75f, true);
```

The third parameter enables access-order mode.

---

### Special Feature: LRU Cache

By overriding:

```java id="p9dx2o"
protected boolean removeEldestEntry(Map.Entry<K,V> eldest)
```

a `LinkedHashMap` can automatically remove the least recently used element, enabling a simple **LRU cache** implementation.

---

### Properties

* Predictable iteration order
* Slightly higher memory usage than `HashMap`
* Performance close to `HashMap` (O(1) average)

---

### Backend Usage

* LRU caching
* Recently accessed data tracking
* Order-sensitive processing

---

## 4. TreeMap

### Internal Working

`TreeMap` is implemented using a **Red-Black Tree**, a self-balancing binary search tree.

The tree automatically maintains sorted order after every insertion and deletion.

---

### Ordering

Keys are sorted based on:

* `Comparable` (natural ordering), or
* A provided `Comparator`

---

### Properties

* Keys are always sorted
* Does **not allow null keys**
* Allows null values
* Not thread-safe
* Time complexity: **O(log n)** for insert, search, and delete

---

### Duplicate Detection

`TreeMap` determines key uniqueness using comparison logic.

If:

```java id="v7y3t2"
compare(key1, key2) == 0
```

the new value replaces the existing entry, even if `equals()` returns false.

---

### Backend Usage

* Sorted data processing
* Range queries
* Leaderboards or ranking systems
* Time-based ordering

---

## 5. Comparison Summary

| Map           | Ordering           | Internal Structure       | Time Complexity |
| ------------- | ------------------ | ------------------------ | --------------- |
| HashMap       | None               | Hash table               | O(1) average    |
| LinkedHashMap | Insertion / Access | Hash table + linked list | O(1) average    |
| TreeMap       | Sorted by key      | Red-Black Tree           | O(log n)        |

---

## 6. Backend Selection Guide

* **HashMap** → default choice for performance
* **LinkedHashMap** → when predictable iteration order is required
* **TreeMap** → when sorted keys or range-based operations are needed

---

## 🧠 Core Mental Model

* `HashMap` → fastest lookup, no order
* `LinkedHashMap` → HashMap + memory of order
* `TreeMap` → always sorted using comparison logic

Hash-based maps depend on `hashCode()` + `equals()`, while tree-based maps depend entirely on comparison logic.

---

