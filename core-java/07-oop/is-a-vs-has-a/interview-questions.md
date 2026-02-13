# Interview Questions – IS-A vs HAS-A

---

## LEVEL 0 – Academic

1. What is IS-A relationship?
2. What is HAS-A relationship?
3. Give examples of each.

---

## LEVEL 1 – Fresher

1. Difference between IS-A and HAS-A?
2. When should inheritance be used?
3. When should composition be used?
4. Can HAS-A achieve polymorphism?

---

## LEVEL 2 – 1–2 YOE

1. How do you test if IS-A relationship is correct?
2. What happens if IS-A is used incorrectly?
3. Explain Rectangle–Square problem.
4. How does IS-A relate to substitutability?
5. Why is HAS-A more flexible?

---

## LEVEL 3 – 2–3 YOE

1. How does violating IS-A break LSP?
2. Give real backend example where IS-A was misused.
3. How does HAS-A improve testability?
4. How does IS-A increase tight coupling?
5. How does this affect microservice design?

---

## Senior / Twisted Questions

1. Can composition replace inheritance completely?
2. Is Square truly a Rectangle?
3. Why is substitutability more important than reuse?
4. Can you achieve code reuse without inheritance?
5. How does IS-A affect memory layout?
6. How does wrong IS-A cause concurrency bugs?

---

## Common Interview Traps

❌ Saying IS-A is always better  
❌ Ignoring substitutability  
❌ Using inheritance only for reuse  
❌ Confusing interface implementation with HAS-A

---

## One Interview-Safe Explanation

> IS-A represents inheritance and requires safe substitutability, while HAS-A represents composition and offers flexibility and loose coupling, which is preferred in modern backend systems.
