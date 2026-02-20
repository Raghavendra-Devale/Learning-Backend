

# Interview Questions – Iterable & Iterator


## Q1. Difference between Iterable and Iterator?

**Answer:**
`Iterable` allows a collection to be used in a for-each loop, while `Iterator` performs the actual traversal of elements.

**Explanation:**
`Iterable` only provides a way to obtain an iterator using `iterator()`.
`Iterator` is the object that moves through the collection using `hasNext()` and `next()`.
This separation keeps data storage and traversal logic independent.

---

## Q2. How does for-each loop work internally?

**Answer:**
The for-each loop internally uses an `Iterator` by calling `iterator()`, `hasNext()`, and `next()`.

**Explanation:**
The loop:

```java
for (Integer x : list) { }
```

is converted by the compiler into:

```java
Iterator<Integer> it = list.iterator();
while (it.hasNext()) {
    Integer x = it.next();
}
```

This is why for-each works only with classes implementing `Iterable`.

---

## Q3. What causes ConcurrentModificationException?

**Answer:**
It occurs when a collection is structurally modified during iteration using a fail-fast iterator.

**Explanation:**
Collections maintain an internal modification count.
If the collection is modified using methods like `add()` or `remove()` while an iterator is traversing it, the iterator detects the change and throws `ConcurrentModificationException` to prevent inconsistent traversal.

---

## Q4. What is the only safe way to remove elements during iteration?

**Answer:**
Using `Iterator.remove()`.

**Explanation:**
`Iterator.remove()` updates the iterator’s internal state along with the collection.
Calling `collection.remove()` directly changes the collection without informing the iterator, causing a modification mismatch and triggering an exception.

---

## Q5. What is a fail-fast iterator?

**Answer:**
A fail-fast iterator throws `ConcurrentModificationException` when the collection is structurally modified during iteration.

**Explanation:**
Fail-fast iterators track modifications using an internal counter.
If the iterator detects that the collection changed unexpectedly, it immediately stops execution to expose potential logical bugs early.

Examples include iterators from `ArrayList`, `HashMap`, and `HashSet`.

---

## Q6. What is a fail-safe iterator?

**Answer:**
A fail-safe iterator does not throw exceptions during concurrent modification and works on a snapshot or weakly consistent view of the data.

**Explanation:**
Instead of failing, these iterators either iterate over a copied snapshot or tolerate changes while iterating.
This allows concurrent updates but may result in outdated or partially updated data being seen by the iterator.

Examples include `CopyOnWriteArrayList` and `ConcurrentHashMap`.

---

## Q7. Why are fail-fast iterators preferred?

**Answer:**
They detect programming errors early and prevent unpredictable behavior.

**Explanation:**
Without fail-fast behavior, modifying a collection during traversal could silently skip elements or produce incorrect results.
Fail-fast iterators immediately signal that iteration rules were violated, making bugs easier to identify during development.

---

## Q8. Why are fail-safe iterators not always ideal?

**Answer:**
They may not reflect the latest updates and can consume extra memory.

**Explanation:**
Snapshot-based iteration requires copying data or maintaining additional structures.
This increases memory usage and may lead to weak consistency where recent modifications are not visible during iteration.

---

## Common Interview Traps & Pitfalls

❌ Saying fail-safe is always better
❌ Removing elements directly inside for-each
❌ Confusing `Iterator.remove()` with `Collection.remove()`
❌ Assuming `ConcurrentModificationException` indicates a JVM issue
❌ Thinking fail-fast provides thread safety

---

## One Interview-Safe Explanation

> “Iterable provides an iterator, and Iterator performs traversal. For-each loops internally use iterators. Most standard collections use fail-fast iterators to detect structural modification early, while concurrent collections use fail-safe or weakly consistent iterators to support concurrency.”

---

