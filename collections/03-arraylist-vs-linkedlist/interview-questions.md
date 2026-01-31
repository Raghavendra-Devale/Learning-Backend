# 🎯 `interview-questions.md` — Lesson 11

# Interview Questions – ArrayList vs LinkedList

---

## Q1. Difference between ArrayList and LinkedList?
**Answer:**
ArrayList uses a dynamic array, while LinkedList uses a doubly linked list.

---

## Q2. Why is ArrayList faster than LinkedList in most cases?
**Answer:**
ArrayList offers O(1) random access and better cache locality due to contiguous memory.

---

## Q3. Is LinkedList always faster for insertion and deletion?
**Answer:**
No. LinkedList insertion/deletion is O(1) only when the node reference is known. By index, it is O(n).

---

## Q4. Which one uses more memory and why?
**Answer:**
LinkedList uses more memory because each node stores extra references to previous and next nodes.

---

## Q5. Which one is better for iteration?
**Answer:**
ArrayList, due to cache-friendly contiguous memory.

---

## Q6. Why is LinkedList rarely used in backend applications?
**Answer:**
Due to high memory overhead, poor cache performance, and lack of fast random access.

---

## Common Interview Traps & Pitfalls

❌ Saying LinkedList is always faster for insert/delete  
❌ Ignoring cache locality  
❌ Choosing LinkedList without knowing access pattern  

---

## One Interview-Safe Explanation

> “ArrayList is generally preferred due to faster random access, lower memory overhead, and better cache locality, while LinkedList is suitable only for specific queue-like use cases.”
