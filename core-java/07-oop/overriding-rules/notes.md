# OOP – Lesson 6
## Method Overriding Rules (Design + JVM Perspective)

Method overriding enables runtime polymorphism.

A subclass provides its own implementation of a parent method.

But strict rules apply.

---

## 1. Basic Conditions for Overriding

To override:
- Method name must be same
- Parameter list must be same
- Method must not be private
- Method must not be final
- Method must not be static

---

## 2. Access Modifier Rule

Overriding method:
- Cannot reduce visibility
- Can increase visibility

Example:
Parent: protected
Child: public (allowed)

Parent: public
Child: protected (not allowed)

Reason:
Substitution principle must not break accessibility.

---

## 3. Checked Exception Rule

Child method:
- Cannot throw broader checked exceptions
- Can throw narrower checked exceptions
- Can throw unchecked exceptions freely

Example:
Parent throws IOException
Child can throw FileNotFoundException
Child cannot throw Exception

Reason:
Caller relying on parent contract must not break.

---

## 4. Covariant Return Type

Child can return:
- Same return type
- Subtype of return type

Example:
Parent: Animal get()
Child: Dog get()

This is called covariant return type.

---

## 5. Final Methods

Final methods:
- Cannot be overridden
- Ensures behavior stability

Used when:
- Logic must not change
- Security-sensitive methods

---

## 6. Static Methods

Static methods:
- Cannot be overridden
- They are hidden (method hiding)
- Resolved at compile time

Polymorphism does not apply to static methods.

---

## 7. Private Methods

Private methods:
- Are not inherited
- Cannot be overridden

They belong only to the class itself.

---

## 8. Constructors

Constructors:
- Cannot be overridden
- Not inherited
- Executed in parent-first order

---

## 9. @Override Annotation

Recommended practice:
Use @Override to:
- Avoid mistakes
- Get compile-time safety

---

## 10. Backend Perspective

Incorrect overriding can:
- Break APIs
- Cause unexpected runtime behavior
- Violate Liskov Substitution Principle
- Introduce security bugs

Framework base classes often rely on correct overriding.

---

## 11. Common Mistakes

- Reducing visibility
- Throwing broader exceptions
- Forgetting @Override
- Confusing static hiding with overriding
- Violating method contract

---

## 12. Interview-Safe Summary

> Method overriding enables runtime polymorphism, but must respect visibility, exception, and return type rules to preserve substitutability and maintain system stability.
