# 🧺 Java Collections — Notes (Interview-Oriented)

These notes explain **what to choose, why to choose it, and how it works internally**.
The focus is on **decision-making, internals, performance, and backend usage**.

---

## 1. Why Collections Exist

Collections provide:
- Dynamic data storage
- Ready-made data structures
- Standardized APIs
- Optimized performance compared to custom implementations

They replace arrays when:
- Size is dynamic
- Operations like insert/delete/search are frequent

---

## 2. Core Interfaces

### Collection
Root interface for List, Set, Queue.

### List
- Ordered
- Allows duplicates
- Index-based access

Common implementations:
- ArrayList
- LinkedList

---

### Set
- No duplicates
- Unordered (mostly)

Common implementations:
- HashSet
- LinkedHashSet
- TreeSet

Uniqueness is ensured using:
- `hashCode()`
- `equals()`

---

### Map
- Key–value pairs
- Keys are unique

Common implementations:
- HashMap
- LinkedHashMap
- TreeMap
- ConcurrentHashMap

Map does not extend Collection.

---

## 3. List Implementations

### ArrayList
- Backed by dynamic array
- O(1) random access
- Slower insert/delete in middle
- Resizing overhead

### LinkedList
- Doubly linked list
- O(n) access
- Fast insert/delete
- Higher memory overhead

---

## 4. Set Implementations

### HashSet
- No order
- Fast (O(1) average)
- Uses HashMap internally

### LinkedHashSet
- Maintains insertion order
- Slightly slower than HashSet

### TreeSet
- Sorted order
- Uses Red-Black Tree
- O(log n)
- No null elements (natural ordering)

---

## 5. Map Implementations

### HashMap
- Fastest lookup
- One null key allowed
- Multiple null values allowed
- Not thread-safe

### LinkedHashMap
- Maintains insertion or access order
- Used for LRU cache

### TreeMap
- Sorted by key
- O(log n)
- No null keys

### ConcurrentHashMap
- Thread-safe
- No null keys or values
- High concurrency using CAS and fine-grained locking

---

## 6. equals() and hashCode()

- hashCode → decides bucket
- equals → decides equality

Rules:
- Equal objects must have same hashCode
- Same hashCode does not mean equal objects

---

## 7. Iterators

### Fail-Fast
- Throws ConcurrentModificationException
- Example: ArrayList iterator

### Fail-Safe
- Works on copy
- Example: CopyOnWriteArrayList
- More memory, slower writes

---

## 8. Queue & Deque

### Queue
- FIFO
- `offer()` preferred over `add()`

### Deque
- Double-ended queue
- Can act as stack or queue
- Preferred over legacy Stack

---

## 9. Concurrency in Collections

- `Collections.synchronizedMap()` → single lock, poor scalability
- `ConcurrentHashMap` → high concurrency, better performance

---

## 10. Memory & Special Collections

### WeakHashMap
- Keys are weakly referenced
- Used for caching
- Entries removed when key is GC’d

---

## 11. Backend Design Principles

- Choose based on:
  - Uniqueness
  - Ordering
  - Access pattern
  - Concurrency
  - Memory

---

## Interview-Safe Summary

> “Collections should be chosen based on uniqueness, ordering, access pattern, concurrency requirements, and memory behavior.”

---
