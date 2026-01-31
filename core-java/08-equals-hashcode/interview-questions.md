
# Interview Questions – equals() & hashCode()

---

## Q1. Difference between `==` and `equals()`?
**Answer:**
`==` compares references, while `equals()` compares logical equality.

---

## Q2. Why must `hashCode()` be overridden when `equals()` is overridden?
**Answer:**
To maintain the contract required by hash-based collections and ensure correct bucket placement.

---

## Q3. Can two unequal objects have the same hashCode?
**Answer:**
Yes. This is called a hash collision and is handled using `equals()`.

---

## Q4. Can two equal objects have different hashCodes?
**Answer:**
No. This violates the hashCode contract and breaks collection behavior.

---

## Q5. How does HashMap use equals() and hashCode() internally?
**Answer:**
`hashCode()` determines the bucket, and `equals()` identifies the exact key.

---

## Q6. What happens if a key’s hashCode changes after insertion?
**Answer:**
The object may become unreachable in the HashMap, causing lookup failures.

---

## Q7. Is hashCode unique for every object?
**Answer:**
No. HashCode uniqueness is not guaranteed.

---

## Common Interview Traps & Pitfalls

❌ Saying equal hashCodes mean equal objects  
❌ Overriding equals() but not hashCode()  
❌ Using mutable fields in hashCode()  
❌ Assuming hashCode is memory address  

---

## One Interview-Safe Explanation

> “`equals()` defines logical equality, while `hashCode()` is used by hash-based collections for bucket placement. Both must be overridden together to ensure correct collection behavior.”

