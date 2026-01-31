# Lesson 9: HashMap Internals (Deep Dive)

This note explains the internal working of `HashMap`, one of the most important topics in Java backend interviews.

---

## 1. What Is HashMap?

HashMap is an implementation of the `Map` interface that stores key–value pairs and provides fast lookup based on hashing.

---

## 2. Internal Structure

Internally, HashMap uses:
- An **array of buckets**
- Each bucket can store:
  - A linked list
  - Or a red-black tree (Java 8+)

```

Array
├── bucket 0 → null
├── bucket 1 → list / tree
├── bucket 2 → list / tree
└── ...

```

---

## 3. How put(key, value) Works

When `put()` is called:

1. `hashCode()` is called on the key
2. Hash value is spread to reduce collisions
3. Bucket index is calculated using:
```

index = hash & (n - 1)

```
4. If bucket is empty → entry is stored
5. If bucket is not empty:
- `equals()` is used to check existing keys
- Value is replaced or new entry is added

---

## 4. Why Capacity Is Always a Power of 2

Using power-of-2 capacity allows HashMap to calculate bucket index using bitwise AND instead of modulo, improving performance and hash distribution.

---

## 5. Collision Handling

### Java 7
- Collisions handled using linked lists
- Worst case: O(n)

### Java 8+
- If bucket size > 8 and table size ≥ 64
- Linked list is converted to a red-black tree
- Worst case improves to O(log n)

---

## 6. Load Factor & Resizing

Default values:
- Initial capacity: 16
- Load factor: 0.75

Resize occurs when:
```

size > capacity × loadFactor

```

Resizing is expensive because all entries are rehashed.

---

## 7. Performance Characteristics

- Average case lookup: O(1)
- Worst case (Java 7): O(n)
- Worst case (Java 8+): O(log n)

---

## 8. Thread Safety

HashMap is **not thread-safe**.
Concurrent modification can lead to:
- Data corruption
- Lost updates
- Infinite loops (pre-Java 8)

Use `ConcurrentHashMap` for concurrent access.

---

## 9. Backend Relevance

HashMap is used heavily in:
- Caching
- Request processing
- Configuration storage
- Framework internals (Spring, Hibernate)

Incorrect usage can lead to subtle production bugs.

