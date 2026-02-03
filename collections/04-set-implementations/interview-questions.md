# Interview Questions – Set Implementations (HashSet, LinkedHashSet, TreeSet)

## Core Understanding

### Q1. What is a Set in Java?
**Answer:**
A Set is a collection that does not allow duplicate elements and does not provide index-based access.

---

### Q2. How does Set detect duplicates?
**Answer:**
- HashSet / LinkedHashSet → `hashCode()` + `equals()`
- TreeSet → `compareTo()` or `Comparator`

---

## HashSet

### Q3. How does HashSet work internally?
**Answer:**
HashSet is backed by a HashMap where elements are stored as keys with a dummy constant value.

---

### Q4. Does HashSet maintain insertion order?
**Answer:**
No. HashSet does not guarantee any ordering.

---

### Q5. How many nulls are allowed in HashSet?
**Answer:**
Only one `null` element is allowed.

---

### Q6. What happens if hashCode is same but equals is false?
**Answer:**
Both elements are stored in the same bucket, and `equals()` is used to differentiate them.

---

## LinkedHashSet

### Q7. How is LinkedHashSet different from HashSet?
**Answer:**
LinkedHashSet maintains insertion order by using a doubly linked list in addition to hashing.

---

### Q8. Is LinkedHashSet slower than HashSet?
**Answer:**
Slightly, due to extra memory overhead, but performance is still close to HashSet.

---

### Q9. When should LinkedHashSet be preferred?
**Answer:**
When uniqueness is required along with predictable iteration order.

---

## TreeSet

### Q10. How does TreeSet work internally?
**Answer:**
TreeSet is backed by a Red-Black Tree and maintains elements in sorted order.

---

### Q11. How does TreeSet detect duplicates?
**Answer:**
TreeSet detects duplicates using comparison results (`compareTo()` or `Comparator`), not `equals()`.

---

### Q12. Can TreeSet contain null?
**Answer:**
No. TreeSet does not allow null elements (except some legacy cases).

---

### Q13. What happens if compareTo returns 0 but equals returns false?
**Answer:**
TreeSet treats the elements as duplicates and ignores the new element.

---

### Q14. Why is TreeSet slower than HashSet?
**Answer:**
Because TreeSet operations have O(log n) complexity due to tree traversal, while HashSet operations are O(1) on average.

---

## Comparable vs Comparator

### Q15. Difference between Comparable and Comparator?
**Answer:**
Comparable defines natural ordering within the class, while Comparator defines external custom ordering.

---

### Q16. Can TreeSet be used without Comparable?
**Answer:**
Yes, if a Comparator is provided during TreeSet creation.

---

### Q17. Can we change sorting logic at runtime?
**Answer:**
Yes, by using different Comparator implementations.

---

## Tricky & Indirect Questions

### Q18. Why can TreeSet “lose” elements?
**Answer:**
Because duplicate detection is based on comparison results, not equals(), and compareTo returning 0 causes element rejection.

---

### Q19. Why should compareTo and equals be consistent?
**Answer:**
Inconsistent implementations can cause unexpected behavior in sorted collections like TreeSet.

---

### Q20. Which Set implementation is fastest?
**Answer:**
HashSet, because it provides O(1) average time complexity.

---

## Common Interview Traps & Pitfalls ⚠️

❌ HashSet maintains order  
❌ TreeSet uses equals()  
❌ Comparator is slower than Comparable  
❌ compareTo must return only -1, 0, 1  
❌ All Set implementations allow null  

---

## One Interview-Safe Summary

> “HashSet provides fast, unordered uniqueness using hashing. LinkedHashSet preserves insertion order. TreeSet maintains sorted order using comparison logic and detects duplicates based on comparison results, not equals.”

---
