# Interview Questions – Method Overriding

---

## LEVEL 0 – Academic

1. What is method overriding?
2. What are the rules for overriding?
3. Can constructors be overridden?
4. What is covariant return type?

---

## LEVEL 1 – Fresher

1. Can access modifier be reduced?
2. Can final methods be overridden?
3. Can static methods be overridden?
4. What happens if signature changes?
5. What is method hiding?

---

## LEVEL 2 – 1–2 YOE

1. Why can't child throw broader checked exception?
2. Why can't visibility be reduced?
3. What is the difference between overloading and overriding?
4. What happens if parent method is private?
5. Why should we use @Override?
6. Can return type change?

---

## LEVEL 3 – 2–3 YOE

1. How does overriding relate to Liskov Substitution Principle?
2. How can wrong overriding break APIs?
3. How does JVM perform dynamic method dispatch?
4. How can overriding introduce security risks?
5. What is bridge method (advanced)?
6. How do generics affect overriding?

---

## Senior / Twisted Questions

1. Can you override a method and throw RuntimeException?
2. What happens if parent method throws no exception?
3. Can abstract method override concrete method?
4. Can concrete method override abstract method?
5. What if parent method is final?
6. Can synchronized modifier be changed?
7. What happens if return type is incompatible?

---

## Common Interview Traps

❌ Saying static methods are overridden  
❌ Forgetting exception rule  
❌ Reducing visibility  
❌ Changing parameter type and calling it overriding  
❌ Not knowing covariant return type

---

## One Interview-Safe Explanation

> Overriding must maintain the parent contract by respecting visibility, checked exceptions, and return type rules, ensuring runtime polymorphism works safely and predictably.
