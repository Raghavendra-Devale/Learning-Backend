# Interview Questions – ConcurrentHashMap

## Q1. Why is HashMap not thread-safe?
**Answer:**
Because concurrent modifications can corrupt its internal structure and cause inconsistent behavior.

---

## Q2. Why is ConcurrentHashMap faster than synchronizedMap?
**Answer:**
Because it uses fine-grained locking and CAS instead of synchronizing the entire map.

---

## Q3. Why does ConcurrentHashMap not allow null keys or values?
**Answer:**
To avoid ambiguity between a missing key and a key mapped to null during concurrent access.

---

## Q4. What happens if two threads update the same key?
**Answer:**
ConcurrentHashMap ensures thread safety, and one update safely overwrites the other without data corruption.

---

## Q5. Does ConcurrentHashMap throw ConcurrentModificationException?
**Answer:**
No. It uses weakly consistent iterators that tolerate concurrent modifications.

---

## Q6. Is ConcurrentHashMap fully lock-free?
**Answer:**
No. Reads are lock-free, but writes may use fine-grained locking.

---

## Common Interview Traps & Pitfalls

❌ Saying ConcurrentHashMap is completely lock-free  
❌ Saying synchronizedMap and ConcurrentHashMap are same  
❌ Assuming HashMap is safe for concurrent reads & writes  
❌ Forgetting null restriction  

---

## One Interview-Safe Explanation

> “ConcurrentHashMap provides thread safety with high concurrency by using fine-grained locking and CAS, allowing safe concurrent access without locking the entire map.”

---