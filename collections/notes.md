


#  Java Collections — Interview-Oriented Notes

These notes focus on **what to choose, why to choose it, and how it works internally**.

The goal is not just API knowledge, but understanding:

* internal data structures
* performance trade-offs
* ordering and uniqueness rules
* real backend usage decisions

---

## 1. Why Collections Exist

Java Collections provide:

* Dynamic data storage
* Ready-made data structures
* Standardized APIs
* Optimized implementations compared to custom structures

Collections are preferred over arrays when:

* Size changes frequently
* Insertions or deletions are common
* Searching and iteration are required
* Abstraction and flexibility are needed

Arrays store data.
Collections manage data behavior.

---

## 2. Core Interfaces

### Collection

Root interface for most collection types:

* `List`
* `Set`
* `Queue`

Defines common operations such as add, remove, and iteration.

---

### List

Characteristics:

* Ordered collection
* Allows duplicates
* Index-based access

Common implementations:

* `ArrayList`
* `LinkedList`

Used when element position matters.

---

### Set

Characteristics:

* No duplicate elements
* Ordering depends on implementation

Common implementations:

* `HashSet`
* `LinkedHashSet`
* `TreeSet`

Uniqueness is enforced using:

* `hashCode()`
* `equals()`

(or comparison logic for sorted sets).

---

### Map

Characteristics:

* Stores key–value pairs
* Keys must be unique
* Values may repeat

Common implementations:

* `HashMap`
* `LinkedHashMap`
* `TreeMap`
* `ConcurrentHashMap`

`Map` is part of the Collections Framework but **does not extend `Collection`**.

---

## 3. List Implementations

### ArrayList

* Backed by a dynamic array
* O(1) random access
* Slower insert/delete in middle due to shifting
* Resizing occurs when capacity grows

Best for read-heavy scenarios.

---

### LinkedList

* Doubly linked list structure
* O(n) access by index
* Fast insertion and deletion once position is known
* Higher memory usage due to node references

Useful when frequent structural modification occurs.

---

## 4. Set Implementations

### HashSet

* No ordering guarantee
* O(1) average performance
* Internally backed by `HashMap`

Best for fast uniqueness checks.

---

### LinkedHashSet

* Maintains insertion order
* Slightly higher memory overhead than `HashSet`
* Predictable iteration order

Useful when order of insertion matters.

---

### TreeSet

* Maintains sorted order
* Implemented using a Red-Black Tree
* O(log n) operations
* Does not allow null elements when natural ordering is used

Uniqueness is determined using comparison logic.

---

## 5. Map Implementations

### HashMap

* Fast key lookup (O(1) average)
* Allows one null key
* Allows multiple null values
* Not thread-safe

Default choice for most backend scenarios.

---

### LinkedHashMap

* Maintains insertion order or access order
* Can be used to implement LRU caching
* Performance close to `HashMap`

Useful when predictable iteration is required.

---

### TreeMap

* Keys stored in sorted order
* O(log n) operations
* Does not allow null keys
* Uses `Comparable` or `Comparator`

Useful for range queries and ordered processing.

---

### ConcurrentHashMap

* Thread-safe map implementation
* Does not allow null keys or values
* Uses fine-grained locking and CAS operations for high concurrency

Preferred for concurrent backend applications.

---

## 6. equals() and hashCode()

In hash-based collections:

* `hashCode()` determines bucket placement
* `equals()` determines logical equality

Rules:

* Equal objects must produce the same hash code
* Same hash code does not guarantee equality

Incorrect implementation leads to lookup failures and duplicate storage.

---

## 7. Iterators

### Fail-Fast Iterators

* Throw `ConcurrentModificationException`
* Detect structural modification during iteration

Example: `ArrayList`, `HashMap`

---

### Fail-Safe Iterators

* Operate on snapshot or weakly consistent view
* Do not throw modification exceptions
* Higher memory or write cost

Example: `CopyOnWriteArrayList`, `ConcurrentHashMap`

---

## 8. Queue & Deque

### Queue

* FIFO (First-In, First-Out)
* `offer()` preferred over `add()` because it avoids exceptions on capacity limits

---

### Deque

* Double-ended queue
* Supports insertion/removal at both ends
* Can act as both stack and queue
* Preferred over legacy `Stack`

---

## 9. Concurrency in Collections

* `Collections.synchronizedMap()` → single lock, limited scalability
* `ConcurrentHashMap` → segmented or fine-grained synchronization for better throughput

Modern concurrent applications favor concurrent collections over synchronized wrappers.

---

## 10. Memory & Special Collections

### WeakHashMap

* Keys are weakly referenced
* Entries removed automatically when keys are garbage collected
* Commonly used for caching and memory-sensitive mappings

---

## 11. Backend Design Principles

Collection choice depends on:

* Uniqueness requirements
* Ordering needs
* Access patterns (read vs write)
* Concurrency requirements
* Memory behavior

Correct collection selection improves both performance and code clarity.

---

## Interview-Safe Summary

> “Collections should be selected based on uniqueness, ordering, access patterns, concurrency needs, and memory characteristics rather than habit or familiarity.”

---
