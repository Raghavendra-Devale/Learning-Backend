
# 📘 `this` and `super` Keyword — Complete Notes

---

## 1. Why `this` and `super` Exist

When working with inheritance and objects, Java needs a way to distinguish:

* current object
* parent object

So Java provides two special references:

```
this  → current class object
super → parent class object
```

They are not variables.
They are **implicit references** created by JVM.

---

## 2. The `this` Keyword

`this` refers to the **current object instance**.

---

### 2.1 Access Current Object Variables

Used when local variable and instance variable share same name.

```java
class Student {
    String name;

    Student(String name){
        this.name = name;
    }
}
```

Without `this`, parameter shadows instance variable.

---

### 2.2 Calling Current Class Method

```java
this.display();
```

Usually optional but improves clarity.

---

### 2.3 Constructor Chaining (Very Important)

One constructor can call another constructor in same class.

```java
class Student {

    Student(){
        this("Unknown");
    }

    Student(String name){
        System.out.println(name);
    }
}
```

Rule:

> `this()` must be first statement in constructor.

---

### Why Constructor Chaining Exists

Avoid code duplication during object initialization.

---

### 2.4 Passing Current Object

```java
someMethod(this);
```

Used in callbacks and frameworks.

---

### 2.5 Returning Current Object

Common in builder pattern:

```java
return this;
```

Used for method chaining.

---

## 3. The `super` Keyword

`super` refers to **parent class object**.

Used only when inheritance exists.

---

### 3.1 Access Parent Class Variable

```java
class Parent {
    int x = 10;
}

class Child extends Parent {
    int x = 20;

    void show(){
        System.out.println(super.x);
    }
}
```

Output:

```
10
```

---

### 3.2 Call Parent Class Method

```java
super.display();
```

Useful when child overrides method but still needs parent logic.

---

### 3.3 Calling Parent Constructor (CRITICAL)

```java
class Parent {
    Parent(){
        System.out.println("Parent constructor");
    }
}

class Child extends Parent {
    Child(){
        super();
        System.out.println("Child constructor");
    }
}
```

---

### Important JVM Rule

If not written explicitly:

```
super()
```

is automatically inserted as first line of child constructor.

---

## 4. Constructor Execution Order

When object is created:

```
Parent constructor runs FIRST
↓
Child constructor runs SECOND
```

Reason:

Parent part of object must exist before child part.

---

### Execution Flow Example

```java
Child c = new Child();
```

Execution:

```
1. Parent constructor
2. Child constructor
```

---

## 5. `this()` vs `super()` Rule

Both must appear as **first statement** in constructor.

You cannot use both together.

❌ Invalid:

```java
this();
super();
```

Compiler error.

Because constructor chaining must form a single path.

---

## 6. Method Overriding & `super`

When child overrides parent method:

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

Allows extending behavior instead of replacing it.

---

## 7. Relationship with Polymorphism

Even though method overriding uses runtime polymorphism:

```
super.method()
```

forces parent implementation explicitly.

---

## 8. Common Compilation Errors

### ❌ Using `this()` not as first statement

```java
System.out.println("Hi");
this();
```

Not allowed.

---

### ❌ Missing Parent Constructor

If parent has parameterized constructor only:

```java
class Parent {
    Parent(int x){}
}
```

Child must call it explicitly:

```java
super(10);
```

Otherwise compilation fails.

---

## 9. Real Backend Usage

You see `super` frequently in:

* Spring controllers
* custom exceptions
* framework extension classes

Example:

```java
public class CustomException extends RuntimeException {
    public CustomException(String msg){
        super(msg);
    }
}
```

Passing message to parent exception class.

---

## 🧠 Mental Model

Imagine object creation like building a house:

```
Parent = foundation
Child  = upper floor
```

Foundation must exist before upper floor.

`super()` builds foundation first.

---

## 10. Key Differences

| Feature             | this           | super                 |
| ------------------- | -------------- | --------------------- |
| Refers to           | Current object | Parent object         |
| Constructor call    | this()         | super()               |
| Access variables    | Current class  | Parent class          |
| Used in inheritance | Optional       | Required conceptually |

---

## ✅ Mastery Checklist

You understand this topic when you can explain:

* why parent constructor runs first
* constructor chaining logic
* difference between this() and super()
* variable shadowing resolution
* overriding behavior with super

---

✅ **Notes Complete**

---
