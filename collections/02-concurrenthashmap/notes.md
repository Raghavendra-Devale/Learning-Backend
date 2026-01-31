
# Lesson 10: ConcurrentHashMap vs HashMap

This note explains the differences between `HashMap`, `Collections.synchronizedMap()`, and `ConcurrentHashMap`, with a focus on thread safety and backend concurrency.

---

## 1. HashMap and Thread Safety

`HashMap` is **not thread-safe**.

Concurrent access can cause:
- Data corruption
- Lost updates
- Infinite loops (pre-Java 8 resize issue)

`HashMap` must never be used for concurrent writes.

---

## 2. Collections.synchronizedMap()

```java
Map<K, V> map = Collections.synchronizedMap(new HashMap<>());
````

### How It Works

* Synchronizes every method on a single lock

### Problems

* Coarse-grained locking
* Poor scalability
* Only one thread can access the map at a time

---

## 3. ConcurrentHashMap

`ConcurrentHashMap` is designed for **high concurrency and thread safety**.

### Key Characteristics

* Thread-safe
* High throughput
* Fine-grained locking
* Lock-free reads

---

## 4. Internal Working (Java 8+)

Java 8 removed segment-based locking.

Modern `ConcurrentHashMap` uses:

* CAS (Compare-And-Swap)
* Synchronized blocks at bucket level
* Locks only when necessary

This allows multiple threads to operate concurrently.

---

## 5. Read vs Write Behavior

### Reads

* Non-blocking
* No locks
* Very fast

### Writes

* CAS first
* Lock only if required
* Limited to specific bucket

---

## 6. Null Keys and Values

`ConcurrentHashMap` does **not allow null keys or values**.

Reason:

* Avoids ambiguity between “key not present” and “key mapped to null” during concurrent access.

---

## 7. Iteration Behavior

* `HashMap` → Fail-fast iterator (`ConcurrentModificationException`)
* `ConcurrentHashMap` → Weakly consistent iterator

Weakly consistent iterators:

* Do not throw exceptions
* May or may not reflect latest updates

---

## 8. Comparison Summary

| Feature     | HashMap              | synchronizedMap | ConcurrentHashMap |
| ----------- | -------------------- | --------------- | ----------------- |
| Thread-safe | ❌                    | ✅               | ✅                 |
| Locking     | None                 | Whole map       | Fine-grained      |
| Performance | High (single thread) | Low             | High              |
| Null keys   | ✅                    | ✅               | ❌                 |

---

## 9. Backend Relevance

Used in:

* Caches
* Session storage
* Metrics
* Configuration
* High-concurrency services

Using `HashMap` in concurrent backend code is a serious design flaw.



