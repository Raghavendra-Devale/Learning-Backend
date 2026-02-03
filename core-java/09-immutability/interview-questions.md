# Interview Questions – Immutability & Defensive Copying

---

## Q1. What is an immutable object?
**Answer:**
An object whose state cannot be changed after it is created.

---

## Q2. Is `final` enough to make a class immutable?
**Answer:**
No. `final` only prevents reassignment, not modification of internal state.

---

## Q3. What is defensive copying?
**Answer:**
Creating a copy of a mutable object instead of exposing internal state directly.

---

## Q4. Why is defensive copying needed in both constructor and getter?
**Answer:**
To prevent external modification of internal state from both input and output paths.

---

## Q5. Why is String immutable?
**Answer:**
For security, thread safety, HashMap key safety, and performance optimizations like string pooling.

---

## Q6. Where should immutability be used in backend systems?
**Answer:**
DTOs, configuration objects, cache keys, value objects, and shared multithreaded data.

---

## Common Interview Traps & Pitfalls

❌ final means immutable  
❌ No setters means immutable  
❌ Defensive copy only needed in getter  
❌ Mutable fields are safe if private  

---

## One Interview-Safe Explanation

> “Immutability ensures an object’s state cannot change after creation, improving thread safety and security. Defensive copying is required to protect internal mutable fields.”

