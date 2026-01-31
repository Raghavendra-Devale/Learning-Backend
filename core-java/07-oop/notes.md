
# Lesson 7: Object-Oriented Programming (OOP) in Java

This note explains OOP concepts from a **backend engineering and interview perspective**, focusing on design, safety, and extensibility rather than definitions.

---

## 1. Class vs Object

### Class
- Blueprint or template
- Loaded once by JVM
- Stored in Method Area (Metaspace)

```java
class User {
    int age;
}
````

---

### Object

* Actual instance of a class
* Created using `new`
* Stored in heap

```java
User u = new User();
```

Many objects can exist for a single class.

---

## 2. Encapsulation

### What Encapsulation Really Means

Encapsulation is about **controlling access to data and enforcing rules**, not just using private variables.

---

### Example

```java
class User {
    private int age;

    public void setAge(int age) {
        if (age < 0) {
            throw new IllegalArgumentException();
        }
        this.age = age;
    }
}
```

Benefits:

* Prevents invalid state
* Centralizes validation
* Improves maintainability

Encapsulation is critical in backend systems where data is shared across requests and threads.

---

## 3. Inheritance

### What Inheritance Is

Inheritance allows one class to reuse and extend another class.

```java
class Employee {
    double salary;
}

class Manager extends Employee {
    int teamSize;
}
```

---

### Problems with Inheritance

* Tight coupling
* Fragile class hierarchies
* Breaking changes propagate easily

---

## 4. Composition (Preferred)

### Composition Over Inheritance

Composition means using other objects instead of extending classes.

```java
class Car {
    Engine engine;
}
```

Benefits:

* Loose coupling
* Better flexibility
* Easier maintenance

---

## 5. Polymorphism

### What Polymorphism Means

Polymorphism allows different implementations to be treated uniformly through a common interface.

```java
Payment p = new CardPayment();
p.pay();
```

At runtime, JVM calls the method of the actual object type using dynamic method dispatch.

---

### Compile-Time vs Runtime

* Method overloading → compile-time
* Method overriding → runtime

---

## 6. Abstraction

Abstraction exposes **what** a class does and hides **how** it does it.

```java
interface Payment {
    void pay();
}
```

Implementations can vary without affecting callers.

---

## 7. Backend Relevance

OOP enables:

* Loose coupling
* Testability
* Safe state management
* Easy refactoring

Frameworks like Spring are built heavily on OOP principles combined with dependency injection.

---



