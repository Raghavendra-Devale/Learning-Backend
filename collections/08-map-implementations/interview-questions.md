# Interview Questions – Map Implementations

---

## Q1. Difference between HashMap and TreeMap?
**Answer:**
HashMap is unordered and faster, while TreeMap maintains sorted order using comparison logic.

---

## Q2. Why does TreeMap not allow null keys?
**Answer:**
Because TreeMap relies on key comparison for ordering, and comparing null would cause a NullPointerException.

---

## Q3. How does TreeMap detect duplicate keys?
**Answer:**
When `compareTo()` or `Comparator.compare()` returns 0.

---

## Q4. Difference between HashMap and LinkedHashMap?
**Answer:**
LinkedHashMap preserves insertion or access order, while HashMap does not guarantee order.

---

## Q5. How can LinkedHashMap be used as an LRU cache?
**Answer:**
By enabling access order and overriding `removeEldestEntry()` to evict the least recently used entry.

---

## Q6. Why is HashMap preferred in backend systems?
**Answer:**
Because it provides O(1) average performance and fast key-value access when ordering is not required.

---

## Common Interview Traps & Pitfalls

❌ TreeMap uses equals for comparison  
❌ LinkedHashMap only supports insertion order  
❌ HashMap maintains order  
❌ All Maps allow null keys  

---

## One Interview-Safe Explanation

> “HashMap provides fast unordered storage, LinkedHashMap preserves predictable order and can support LRU caching, and TreeMap maintains sorted keys using comparison logic with higher cost.”

---
