# Lesson 20: Cloning, Shallow Copy vs Deep Copy

This note explains object copying in Java, the difference between shallow and deep copy, problems with `clone()`, and safer alternatives used in backend systems.

---

## 1. Assignment Is NOT Copying

```java
User u1 = new User();
User u2 = u1;
````

This does not create a new object.
Both references point to the same object.

Any change via one reference affects the other.

---

## 2. Shallow Copy

A shallow copy:

* Creates a new object
* Copies primitive fields
* Copies references to other objects (not the objects themselves)

Example:

```java
User → Address
```

After shallow copy:

* Both User objects share the same Address reference

---

## 3. Deep Copy

A deep copy:

* Creates a new object
* Copies primitive fields
* Creates new copies of referenced objects

Result:

* No shared mutable state
* Changes in one object do not affect the other

---

## 4. clone() Method

Java provides `clone()` via `Cloneable`.

Problems with `clone()`:

* Shallow copy by default
* Constructors are not called
* Poorly designed API
* Error-prone for deep copying

Because of these issues, `clone()` is generally discouraged.

---

## 5. Shallow vs Deep Copy – When to Use

### Shallow Copy Is Safe When:

* Object contains only primitives
* Object contains references to immutable objects

### Deep Copy Is Required When:

* Object contains references to mutable objects
* Independent state is required

---

## 6. Better Alternatives to clone()

Preferred approaches:

* Copy constructors
* Factory methods
* Explicit deep copy logic

These approaches are clearer, safer, and easier to maintain.

---

## 7. Backend Relevance

Incorrect copying can cause:

* Data corruption
* Thread-safety issues
* Hidden side effects

Senior developers avoid `clone()` and prefer explicit copying.

---

## 8. Interview-Safe Summary

> “Assignment copies references, shallow copy shares referenced objects, and deep copy duplicates the entire object graph. Java’s clone() performs shallow copy by default and is generally avoided in favor of explicit copy constructors.”

---


