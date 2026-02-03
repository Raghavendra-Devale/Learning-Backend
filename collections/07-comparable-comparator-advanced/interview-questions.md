# Interview Questions – Comparable vs Comparator (Advanced)

---

## Q1. Why can TreeSet silently drop elements?
**Answer:**
Because TreeSet uses comparison logic for uniqueness, and a comparison result of 0 treats elements as duplicates.

---

## Q2. Why is subtraction-based comparison dangerous?
**Answer:**
Because it can cause integer overflow and incorrect ordering.

---

## Q3. When should Comparable be avoided?
**Answer:**
When multiple sorting strategies are required or ordering depends on context.

---

## Q4. Why must compareTo be consistent with equals?
**Answer:**
To prevent data loss or overwriting in sorted collections like TreeSet and TreeMap.

---

## Q5. Can Comparator affect uniqueness in TreeSet?
**Answer:**
Yes. Comparator determines both ordering and uniqueness in TreeSet.

---

## Q6. Can TreeSet ordering be changed after creation?
**Answer:**
No. Comparator is fixed at creation time.

---

## Common Interview Traps & Pitfalls

❌ Using subtraction in compareTo  
❌ Assuming TreeSet uses equals  
❌ Ignoring consistency with equals  
❌ Believing Comparator does not affect uniqueness  

---

## One Interview-Safe Explanation

> “Comparable defines natural ordering, while Comparator provides flexible external ordering. In sorted collections, comparison logic determines both ordering and uniqueness, so it must be consistent with equals to avoid silent bugs.”

---
