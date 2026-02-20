

# 🎯 Interview Questions — Set Implementations (Refined + Explained)


## Core Understanding

### Q1. What is a Set in Java?



A `Set` is a collection that stores only unique elements and does not support index-based access. The definition of uniqueness depends on the specific Set implementation.

🧠 **Key insight**

Interviewers like hearing that *uniqueness is implementation-dependent*. That shows deeper understanding.

---

### Q2. How does Set detect duplicates?



* `HashSet` / `LinkedHashSet` → use `hashCode()` to locate elements and `equals()` to confirm equality.
* `TreeSet` → uses `compareTo()` or a provided `Comparator` to determine duplicates.

🧠 Translation:

Hash-based sets check **logical equality**.
Tree-based sets check **ordering equality**.

Two very different ideas.

---

# HashSet

---

### Q3. How does HashSet work internally?



HashSet internally uses a HashMap where each element is stored as a key and a constant dummy object is used as the value.

Hidden bonus line (great in interviews):

> Therefore, HashSet inherits HashMap’s hashing and collision-handling behavior.

---

### Q4. Does HashSet maintain insertion order?

✅ Correct: **No**.

Add nuance:

Iteration order may even change after resizing because bucket distribution changes.

---

### Q5. How many nulls are allowed in HashSet?

✅ One `null` element.

Reason:

HashMap allows one null key.

---

### Q6. What happens if hashCode is same but equals is false?



Both elements are stored in the same bucket, and `equals()` is used to distinguish them, so both can exist in the set.

🧠 Important implication:

Hash collisions are normal and expected.

---

# LinkedHashSet

---

### Q7. How is LinkedHashSet different from HashSet?



LinkedHashSet maintains insertion order by combining hashing with a doubly linked list that links entries in insertion sequence.

Key phrase interviewers like:

> predictable iteration order.

---

### Q8. Is LinkedHashSet slower than HashSet?


Slightly slower due to maintaining the linked structure, but time complexity remains close to HashSet for most operations.

Real-world truth: difference is usually negligible.

---

### Q9. When should LinkedHashSet be preferred?


Add practical framing:

* deterministic API responses
* ordered deduplication
* stable test outputs

Backend engineers care about reproducibility.

---

# TreeSet

---

### Q10. How does TreeSet work internally?

✅ Correct:

TreeSet is backed by a Red-Black Tree and maintains sorted order.

Extra insight:

Self-balancing ensures tree height stays logarithmic.

---

### Q11. How does TreeSet detect duplicates?



Duplicates are determined when comparison returns `0`, not by `equals()`.

This is one of the most common interview traps.

---

### Q12. Can TreeSet contain null?

✅ No (modern Java).

Reason:

Tree comparisons require calling comparison logic; `null` cannot be compared safely.

---

### Q13. What happens if compareTo returns 0 but equals returns false?



Add interpretation:

TreeSet considers them the same position in ordering, so the second element is rejected.

This is why comparison must represent logical equality.

---

### Q14. Why is TreeSet slower than HashSet?



TreeSet operations require tree traversal and rebalancing, resulting in O(log n) complexity, whereas HashSet uses hashing with O(1) average performance.

---

# Comparable vs Comparator

---

### Q15. Difference between Comparable and Comparator?



Comparable defines natural ordering inside the class using `compareTo()`, while Comparator provides external customizable ordering using `compare()`.

---

### Q16. Can TreeSet be used without Comparable?

✅ Yes.

If a Comparator is supplied at construction.

Example mental model:

TreeSet must always know *how to compare* elements somehow.

---

### Q17. Can we change sorting logic at runtime?

✅ Yes — by creating TreeSets with different Comparator implementations.

Important nuance:

You cannot change ordering of an existing TreeSet without recreating it.

---

# Tricky & Indirect Questions

---

### Q18. Why can TreeSet “lose” elements?



Refinement:

Elements are rejected when comparison returns 0 because TreeSet assumes they occupy the same sorted position.

---

### Q19. Why should compareTo and equals be consistent?



If comparison and equality logic disagree, sorted collections may behave unpredictably, causing missing elements or incorrect lookups.

Rule of thumb:

```text
compareTo(x) == 0  ⇒  equals(x) should be true
```

Not strictly required by compiler — but required for sanity.

---

### Q20. Which Set implementation is fastest?

✅ HashSet (average case).

Add nuance:

Fastest for lookup and insertion when ordering is not required.

---

# 🚫 Interview Trap Awareness (Expanded Meaning)

These traps test conceptual clarity:

* HashSet ≠ ordered collection
* TreeSet equality ≠ equals()
* Comparator overhead is negligible
* compareTo returns any negative/positive value
* Null handling differs across implementations

---

# 🧠 One Polished Interview Summary

> HashSet provides fast uniqueness using hashing, LinkedHashSet maintains insertion order with minimal overhead, and TreeSet maintains sorted order using comparison logic where duplicates are determined by comparison results rather than equals.

---

## The Deeper Insight Behind All Sets

HashSet answers:

> “Are these objects the same?”

TreeSet answers:

> “Do these objects occupy the same position in an ordering?”

That distinction mirrors real systems:

* Hash indexes (databases) → HashSet thinking
* B-tree indexes → TreeSet thinking

Java collections are quietly teaching database architecture principles in miniature.
