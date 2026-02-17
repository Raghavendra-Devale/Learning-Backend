

# 📘 Java Enums — Complete Notes

---

## 1. What is an Enum?

Enum (short for *enumeration*) represents a **fixed set of constants**.

Example:

```java
enum Day {
    MONDAY, TUESDAY, WEDNESDAY
}
```

Usage:

```java
Day today = Day.MONDAY;
```

---

## 2. Why Enums Exist

Before enums, developers used constants:

```java
public static final int MONDAY = 1;
```

Problems:

* no type safety
* invalid values possible
* harder to read and maintain

Enums solve this by creating a restricted set of valid values.

---

## 3. Enum is a Special Class

This is the most important concept:

> Enum is not just constants — it is a class.

When you write:

```java
enum Status {
    SUCCESS, FAILED
}
```

Java internally creates:

* objects of type `Status`
* fixed instances created once by JVM

---

### Key Properties

* implicitly extends `java.lang.Enum`
* constructors are private
* objects cannot be created using `new`
* instances are created only once

---

## 4. Enum Object Behavior

Each enum constant is an object.

```java
Status s = Status.SUCCESS;
```

This is similar to:

```
public static final Status SUCCESS = new Status();
```

But controlled by JVM.

---

## 5. Enum Methods (Built-in)

### `values()`

Returns all enum constants.

```java
for(Status s : Status.values()){
    System.out.println(s);
}
```

---

### `valueOf()`

Converts String → enum.

```java
Status s = Status.valueOf("SUCCESS");
```

---

### `ordinal()`

Returns position index.

```java
Status.SUCCESS.ordinal(); // 0
```

(Not recommended for business logic because order may change.)

---

### `name()`

Returns constant name.

```java
Status.SUCCESS.name();
```

---

## 6. Enums in Switch Statements

```java
switch(status){
    case SUCCESS:
        System.out.println("Done");
        break;
}
```

Cleaner than integer constants.

---

## 7. Enum with Fields (VERY IMPORTANT)

Enums can have variables.

```java
enum Status {
    SUCCESS(200),
    FAILED(500);

    int code;

    Status(int code){
        this.code = code;
    }
}
```

Each constant now stores data.

---

## 8. Enum with Methods

```java
enum Status {
    SUCCESS, FAILED;

    public boolean isSuccess(){
        return this == SUCCESS;
    }
}
```

Enums can contain behavior.

---

## 9. Enum Constructor Rules

* Always private (implicitly)
* Cannot be public
* Called automatically when enum loads

You cannot do:

```java
new Status();
```

Compilation error.

---

## 10. Enum Memory Model

Enum objects are created:

```
once per JVM
```

They behave like singletons.

This makes enums:

* memory efficient
* thread-safe

---

## 11. Enum vs String Comparison

Bad approach:

```java
if(status.equals("SUCCESS"))
```

Good approach:

```java
if(status == Status.SUCCESS)
```

Enum comparison using `==` is safe because only one instance exists.

---

## 12. Enum Singleton Pattern (Interview Favorite)

Enums provide safest singleton implementation.

```java
enum DatabaseConnection {
    INSTANCE;
}
```

JVM guarantees:

* single instance
* serialization safety
* thread safety

---

## 13. Real Backend Usage

Enums commonly represent:

* API status codes
* order states
* user roles
* payment status
* request types

Example:

```java
enum OrderStatus {
    CREATED,
    PAID,
    SHIPPED,
    DELIVERED
}
```

Prevents invalid states like `"shippped"` typo bugs.

---

## 14. Why Enums Are Better Than Constants

| Feature           | Constants | Enum |
| ----------------- | --------- | ---- |
| Type Safety       | ❌         | ✅    |
| Readability       | Medium    | High |
| Methods allowed   | ❌         | ✅    |
| Restricted values | ❌         | ✅    |

---

## 15. Important Internal Fact

Enum implicitly extends:

```
java.lang.Enum
```

Therefore:

❌ Enum cannot extend another class.

(Java doesn't support multiple inheritance.)

---

## 🧠 Mental Model

Think of enum as:

```
A class with limited predefined objects.
```

Not variables — predefined instances.

---

## ✅ Mastery Checklist

You understand enums when you can explain:

* enum is a class, not constant list
* why constructors are private
* why `==` works safely
* how enums improve API safety
* enum singleton advantage

---
