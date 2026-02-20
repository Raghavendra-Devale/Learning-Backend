
# Interview Questions – Map Implementations


## Q1. Difference between HashMap and TreeMap?

**Answer:**
`HashMap` is unordered and provides faster average performance, while `TreeMap` maintains keys in sorted order using comparison logic.

**Explanation:**
`HashMap` stores entries using hashing (`hashCode()` + `equals()`), enabling average O(1) lookup time.
`TreeMap` stores entries in a Red-Black Tree, keeping keys sorted at all times, which results in O(log n) operations due to tree balancing.

---

## Q2. Why does TreeMap not allow null keys?

**Answer:**
Because `TreeMap` relies on key comparison for ordering, and comparing `null` causes a `NullPointerException`.

**Explanation:**
During insertion, `TreeMap` must compare keys to determine their position in the tree.
Since comparison methods like `compareTo()` cannot operate on `null`, Java disallows null keys to prevent runtime comparison failures.

---

## Q3. How does TreeMap detect duplicate keys?

**Answer:**
When `compareTo()` or `Comparator.compare()` returns `0`.

**Explanation:**
`TreeMap` uses comparison results to determine both ordering and uniqueness.
If comparison returns `0`, the map assumes the keys are identical and replaces the existing value instead of adding a new entry.

---

## Q4. Difference between HashMap and LinkedHashMap?

**Answer:**
`LinkedHashMap` preserves insertion or access order, while `HashMap` does not guarantee iteration order.

**Explanation:**
`LinkedHashMap` internally maintains a doubly linked list connecting entries, allowing predictable iteration order.
`HashMap` only uses hashing, so iteration order depends on bucket structure and may change over time.

---

## Q5. How can LinkedHashMap be used as an LRU cache?

**Answer:**
By enabling access-order mode and overriding `removeEldestEntry()` to remove the least recently used entry.

**Explanation:**
When access order is enabled, every `get()` or `put()` moves the accessed entry to the end of the linked list.
Overriding `removeEldestEntry()` allows automatic eviction of the oldest unused entry, implementing LRU behavior efficiently.

---

## Q6. Why is HashMap preferred in backend systems?

**Answer:**
Because it provides O(1) average performance and fast key–value access when ordering is not required.

**Explanation:**
Most backend operations prioritize quick lookup rather than sorted data.
`HashMap` minimizes computation cost compared to tree-based structures, making it ideal for caching, configuration storage, and request processing.

---

## Common Interview Traps & Pitfalls

❌ Assuming `TreeMap` uses `equals()` for key comparison
❌ Thinking `LinkedHashMap` only supports insertion order (it also supports access order)
❌ Believing `HashMap` maintains insertion order
❌ Assuming all `Map` implementations allow null keys
❌ Forgetting that `TreeMap` comparison defines uniqueness

---

## One Interview-Safe Explanation

> “HashMap provides fast unordered storage using hashing, LinkedHashMap preserves predictable iteration order and can support LRU caching, and TreeMap maintains sorted keys using comparison logic with higher computational cost.”

---

