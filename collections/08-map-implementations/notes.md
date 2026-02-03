# Lesson 16: Map Implementations in Java

This note explains the differences between `HashMap`, `LinkedHashMap`, and `TreeMap`, focusing on internal working, ordering, performance, and backend use cases.

---

## 1. Map Basics

A Map stores key–value pairs where:
- Keys are unique
- Values can be duplicated

Uniqueness and ordering depend on the implementation.

---

## 2. HashMap

### Internal Working
- Uses a hash table
- Key placement based on `hashCode()` and `equals()`

### Properties
- No ordering guarantee
- Allows one null key
- Allows multiple null values
- Average time complexity: O(1)

### Backend Usage
- Caching
- Fast lookups
- Configuration storage

---

## 3. LinkedHashMap

### Internal Working
- HashMap + doubly linked list

### Ordering Modes
- Insertion order
- Access order

### Special Feature (LRU Cache)
By enabling access order and overriding `removeEldestEntry()`, LinkedHashMap can implement an LRU cache.

### Properties
- Predictable iteration order
- Slightly higher memory overhead
- Performance close to HashMap

---

## 4. TreeMap

### Internal Working
- Backed by a Red-Black Tree

### Ordering
- Sorted by key
- Uses `Comparable` or `Comparator`

### Properties
- No null keys
- Values can be null
- Time complexity: O(log n)

### Duplicate Detection
TreeMap treats keys as duplicates when comparison returns 0.

---

## 5. Comparison Summary

| Map | Ordering | Internal DS | Time |
|----|---------|-------------|------|
| HashMap | None | Hash table | O(1) |
| LinkedHashMap | Insertion / Access | Hash table + list | O(1) |
| TreeMap | Sorted | Red-Black Tree | O(log n) |

---

## 6. Backend Selection Guide

- HashMap → default choice
- LinkedHashMap → order-sensitive logic
- TreeMap → sorted keys or range queries

---



