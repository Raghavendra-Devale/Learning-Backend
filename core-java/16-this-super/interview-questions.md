

# 🎯 `this` and `super` — Interview Questions & Tricky Scenarios

Goal:

* Understand constructor execution order
* Predict inheritance behavior
* Avoid common polymorphism traps
* Remove confusion around constructor chaining

---

## ✅ Level 1 — Direct Interview Questions

---

### 1. What does `this` keyword represent?

`this` refers to the **current object instance**.

Used to:

* access instance variables
* call methods
* call constructors
* return current object

---

### 2. What does `super` keyword represent?

`super` refers to the **immediate parent class object**.

Used to:

* access parent variables
* call parent methods
* invoke parent constructor

---

### 3. Difference between `this()` and `super()`?

| Feature  | this()                    | super()                    |
| -------- | ------------------------- | -------------------------- |
| Calls    | current class constructor | parent class constructor   |
| Usage    | constructor chaining      | inheritance initialization |
| Position | must be first statement   | must be first statement    |

---

### 4. Can we use both `this()` and `super()` in same constructor?

❌ No.

Only one constructor call can exist as first statement.

---

### 5. Why does parent constructor execute first?

Because child object contains parent part internally.

Parent must initialize before child.

---

## 🧠 Level 2 — Conceptual Understanding

---

### 6. What happens if we don’t write `super()`?

Compiler automatically inserts:

```java
super();
```

as first statement.

---

### 7. When does compilation fail related to `super()`?

If parent has only parameterized constructor:

```java
class Parent {
    Parent(int x){}
}
```

Child must explicitly call:

```java
super(10);
```

Otherwise compilation error.

---

### 8. Why is `this` needed when variable names clash?

```java
Student(String name){
    this.name = name;
}
```

Parameter shadows instance variable.

`this` resolves ambiguity.

---

## ⚠️ Level 3 — Classic Interview Traps

---

### 9. Predict Output

```java
class Parent {
    Parent(){
        System.out.println("Parent");
    }
}

class Child extends Parent {
    Child(){
        System.out.println("Child");
    }
}

public class Test {
    public static void main(String[] args){
        new Child();
    }
}
```

✅ Output:

```
Parent
Child
```

Parent constructor always runs first.

---

### 10. Constructor Chaining

```java
class A {
    A(){
        this(10);
        System.out.println("Default");
    }

    A(int x){
        System.out.println("Parameterized");
    }
}
```

Output:

```
Parameterized
Default
```

---

### 11. Illegal Constructor Call

```java
A(){
    System.out.println("Hello");
    this(10);
}
```

❌ Compilation error.

Constructor call must be first statement.

---

### 12. Variable Shadowing Trap

```java
class Test {
    int x = 10;

    Test(int x){
        x = x;
    }
}
```

Instance variable never updated.

Correct:

```java
this.x = x;
```

---

### 13. Method Overriding with super

```java
class Parent {
    void show(){
        System.out.println("Parent");
    }
}

class Child extends Parent {
    void show(){
        super.show();
        System.out.println("Child");
    }
}
```

Output:

```
Parent
Child
```

---

## 🧩 Level 4 — Deep Interview Questions

---

### 14. Can `this` be used in static methods?

❌ No.

Static methods belong to class, not object.

No current instance exists.

---

### 15. Can `super` be used in static methods?

❌ No.

Requires object inheritance context.

---

### 16. Which executes first: instance variables or constructor?

Order:

```
1. Parent instance variables
2. Parent constructor
3. Child instance variables
4. Child constructor
```

---

### 17. Predict Output (Execution Order Trap)

```java
class Parent {
    int x = print();

    int print(){
        System.out.println("Parent Variable");
        return 10;
    }

    Parent(){
        System.out.println("Parent Constructor");
    }
}

class Child extends Parent {
    Child(){
        System.out.println("Child Constructor");
    }
}
```

Output:

```
Parent Variable
Parent Constructor
Child Constructor
```

---

### 18. Can constructor be overridden?

❌ No.

Constructors are not inherited.

They can only be called using `super()`.

---

### 19. Why `super()` cannot appear twice?

Constructor chain must form a single initialization path.

Multiple parent calls would break object creation logic.

---

### 20. Real Backend Example

Custom exception creation:

```java
class ApiException extends RuntimeException {
    ApiException(String msg){
        super(msg);
    }
}
```

Passing message to parent exception constructor.

Very common in Spring applications.

---

## 🧪 Ultimate Brain Teaser

Predict:

```java
class A {
    A(){
        System.out.println("A");
    }
}

class B extends A {
    B(){
        this(10);
        System.out.println("B");
    }

    B(int x){
        System.out.println("Parameterized B");
    }
}
```

Execution:

```
A
Parameterized B
B
```

Reason:

* `this(10)` called first
* which implicitly calls `super()`
* parent constructor executes first

---

## 🧠 Interviewer’s Hidden Goal

They want to see whether you understand:

* object construction lifecycle
* inheritance initialization
* execution order reasoning

Not syntax — execution flow.

---

## ✅ Mastery Checklist

You are strong when you can explain without hesitation:

* constructor execution order
* automatic super() insertion
* difference between this and super references
* why parent initializes first

---
