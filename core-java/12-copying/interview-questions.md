# Interview Questions – Cloning, Shallow Copy vs Deep Copy
---

## Q1. Is assignment (`=`) a copy in Java?
**Answer:**
No. Assignment copies the reference, not the object.

---

## Q2. What is a shallow copy?
**Answer:**
A shallow copy creates a new object but shares references to nested objects.

---

## Q3. What is a deep copy?
**Answer:**
A deep copy creates a new object and new copies of all referenced objects.

---

## Q4. Why is clone() discouraged?
**Answer:**
Because it performs shallow copy by default, bypasses constructors, and is hard to implement correctly.

---

## Q5. When is shallow copy safe?
**Answer:**
When all referenced fields are immutable.

---

## Q6. When is deep copy required?
**Answer:**
When the object contains mutable referenced fields and independent state is needed.

---

## Common Interview Traps & Pitfalls

❌ Assignment is copying  
❌ clone() creates deep copy  
❌ Shallow copy is always unsafe  
❌ Deep copy is always required  

---

## One Interview-Safe Explanation

> “Shallow copy shares referenced objects, while deep copy duplicates the entire object graph. Because clone() is shallow and bypasses constructors, explicit copy constructors are preferred.”

---