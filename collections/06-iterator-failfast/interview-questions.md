
# Interview Questions – Iterable & Iterator

---

## Q1. Difference between Iterable and Iterator?
**Answer:**
Iterable allows a collection to be used in a for-each loop, while Iterator performs the actual traversal.

---

## Q2. How does for-each loop work internally?
**Answer:**
It uses an Iterator internally by calling iterator(), hasNext(), and next().

---

## Q3. What causes ConcurrentModificationException?
**Answer:**
Structural modification of a collection during iteration using a fail-fast iterator.

---

## Q4. What is the only safe way to remove elements during iteration?
**Answer:**
Using `Iterator.remove()`.

---

## Q5. What is a fail-fast iterator?
**Answer:**
An iterator that throws ConcurrentModificationException when the collection is structurally modified during iteration.

---

## Q6. What is a fail-safe iterator?
**Answer:**
An iterator that does not throw exceptions during concurrent modification and works on a snapshot or weakly consistent view.

---

## Q7. Why are fail-fast iterators preferred?
**Answer:**
They detect bugs early and prevent unpredictable behavior or silent data corruption.

---

## Q8. Why are fail-safe iterators not always ideal?
**Answer:**
They may not reflect latest updates and consume extra memory, leading to weaker consistency.

---

## Common Interview Traps & Pitfalls

❌ Saying fail-safe is always better  
❌ Removing elements directly inside for-each  
❌ Confusing Iterator.remove() with Collection.remove()  
❌ Assuming ConcurrentModificationException is a JVM bug  

---

## One Interview-Safe Explanation

> “Iterable enables for-each iteration, Iterator performs traversal. Most collections use fail-fast iterators to detect concurrent modification early, while concurrent collections use fail-safe or weakly consistent iterators.”

---