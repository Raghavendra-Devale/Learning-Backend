## OOP – Lesson 2: Encapsulation (Complete Interview Coverage)


# Interview Questions – Encapsulation

---

## LEVEL 0 – Academic

1. What is encapsulation?
2. Why do we use private fields?
3. What is data hiding?

---

## LEVEL 1 – Fresher

1. Difference between encapsulation and abstraction?
2. Why are getters and setters used?
3. Can encapsulation exist without private variables?
4. What happens if fields are public?

---

## LEVEL 2 – 1–2 YOE

1. What is an invariant?
2. How does encapsulation protect invariants?
3. Why are excessive setters bad design?
4. How does encapsulation improve maintainability?
5. How can exposing collections break encapsulation?
6. Why is immutability considered strong encapsulation?

---

## LEVEL 3 – 2–3 YOE

1. How does broken encapsulation cause race conditions?
2. How does encapsulation affect thread safety?
3. Should domain entities expose setters?
4. How does encapsulation relate to DDD?
5. What are real-world examples of poor encapsulation?
6. How do frameworks sometimes accidentally break encapsulation?

---

## Senior / Twisted Questions

1. Is encapsulation only about access modifiers?
2. Can you achieve encapsulation without OOP?
3. How does returning internal references break encapsulation?
4. Why is exposing internal state dangerous in concurrent systems?
5. How does immutability eliminate synchronization needs?
6. Can encapsulation increase complexity?

---

## Common Interview Traps

❌ Saying encapsulation = private variables  
❌ Generating setters for every field  
❌ Returning internal mutable collections  
❌ Ignoring concurrency implications  
❌ Confusing abstraction with encapsulation  

---

## One Interview-Safe Explanation

> Encapsulation ensures objects control their own state by exposing only safe operations, protecting invariants, and reducing unintended mutations, especially in concurrent systems.