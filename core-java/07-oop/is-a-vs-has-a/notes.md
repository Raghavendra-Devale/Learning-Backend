# OOP – Lesson 8
## IS-A vs HAS-A (Design-Level Understanding)

IS-A and HAS-A define relationships between classes.

Choosing the wrong one leads to poor design.

---

## 1. IS-A Relationship

IS-A represents inheritance.

Example:
Dog IS-A Animal

Meaning:
Dog is a specialized form of Animal.

If subclass cannot replace superclass without breaking behavior,
IS-A is incorrect.

IS-A implies substitutability.

---

## 2. HAS-A Relationship

HAS-A represents composition.

Example:
Car HAS-A Engine

Meaning:
Car contains Engine as a component.

HAS-A enables:
- Flexibility
- Loose coupling
- Replaceable behavior

---

## 3. The Substitution Test (Critical)

To check IS-A:
Ask:

Can the child safely replace the parent everywhere?

If yes → valid IS-A  
If no → use HAS-A

This leads to Liskov Substitution Principle.

---

## 4. Incorrect IS-A Example

Rectangle and Square example.

Square extends Rectangle:
But if Rectangle allows width and height independently,
Square breaks behavior expectations.

Thus:
Square is not a perfect IS-A Rectangle in design terms.

---

## 5. Why Developers Misuse IS-A

Common mistakes:
- Using inheritance for reuse
- Ignoring behavioral contracts
- Designing without substitution thinking

---

## 6. Real Backend Example

Bad:
class MyService extends BaseService

Good:
class MyService {
private Validator validator;
}

If behavior is not true specialization,
inheritance is wrong choice.

---

## 7. IS-A vs HAS-A in Frameworks

Frameworks use:
- IS-A for type hierarchy
- HAS-A for dependencies

Spring beans:
Mostly HAS-A via dependency injection.

---

## 8. Relationship to LSP

Liskov Substitution Principle states:

Subtypes must be substitutable for their base types.

If IS-A breaks behavior,
LSP is violated.

---

## 9. Design Rule

Use IS-A when:
- Subtype is true specialization
- Behavior is compatible
- Substitution is safe

Use HAS-A when:
- You need flexibility
- Behavior may change
- You want loose coupling

---

## 10. Interview-Safe Summary

> IS-A defines inheritance and requires safe substitutability, while HAS-A defines composition and provides flexibility and loose coupling.
