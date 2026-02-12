# Default and Static Methods in Interfaces  Complete Notes 

---

# 1. Why Were They Introduced?

Before Java 8, interfaces could only contain:

* Abstract methods
* Constants

If a new method was added to an existing interface, all implementing classes were forced to implement it — which broke backward compatibility.

This became a major problem when enhancing core APIs like Collections.

Default and static methods were introduced in Java 8 to:

* Support backward compatibility
* Allow API evolution
* Add behavior to interfaces without breaking existing implementations

---

# 2. Default Methods

A default method is a method inside an interface that has a concrete implementation.

---

## Syntax

```java
interface Vehicle {
    default void stop() {
        System.out.println("Stopping");
    }
}
```

---

## Characteristics

* Inherited by implementing classes
* Can be overridden
* Helps in extending interfaces safely
* Supports multiple inheritance resolution

---

## Example

```java
class Car implements Vehicle {
    // stop() is inherited automatically
}
```

If needed, the class can override:

```java
@Override
public void stop() {
    System.out.println("Car stopping");
}
```

---

# 3. Diamond Problem (Multiple Inheritance Conflict)

If two interfaces provide the same default method:

```java
interface A {
    default void show() {
        System.out.println("A");
    }
}

interface B {
    default void show() {
        System.out.println("B");
    }
}
```

And a class implements both:

```java
class Test implements A, B {
}
```

Compilation error occurs because Java cannot decide which implementation to use.

---

## Resolution

The class must override the method explicitly:

```java
class Test implements A, B {

    @Override
    public void show() {
        A.super.show(); // or B.super.show();
    }
}
```

Important rule:

Class must resolve ambiguity explicitly.

---

# 4. Static Methods in Interfaces

Static methods can also be defined inside interfaces starting from Java 8.

---

## Syntax

```java
interface MathUtils {
    static int square(int x) {
        return x * x;
    }
}
```

---

## Characteristics

* Not inherited by implementing classes
* Cannot be overridden
* Accessed using interface name
* Belongs to the interface itself

---

## Usage

```java
int result = MathUtils.square(5);
```

You cannot call it using an object reference.

---

# 5. Default vs Static — Comparison

| Feature               | Default Method  | Static Method  |
| --------------------- | --------------- | -------------- |
| Has implementation    | Yes             | Yes            |
| Inherited by class    | Yes             | No             |
| Can be overridden     | Yes             | No             |
| Called via            | Object instance | Interface name |
| Supports polymorphism | Yes             | No             |

---

# 6. Rules of Method Resolution

When calling a method:

1. Class methods have highest priority.
2. If no class method, most specific interface default method is chosen.
3. If conflict exists, class must override explicitly.

This ensures predictable behavior.

---

# 7. Backend Usage

---

## Default Methods

Used for:

* Evolving APIs without breaking implementations
* Adding common behavior to interfaces
* Template-style default logic

Example:

```java
interface Auditable {
    default void log(String message) {
        System.out.println("Audit: " + message);
    }
}
```

---

## Static Methods

Used for:

* Utility/helper methods related to interface
* Factory methods

Example:

```java
interface Validator {
    static boolean isValidEmail(String email) {
        return email.contains("@");
    }
}
```

---

# 8. Real-World Example (Java Collections)

Java 8 added methods like:

* `forEach()`
* `stream()`
* `removeIf()`

These were added as default methods in `Collection` interface to maintain backward compatibility.

---

# 9. Important Interview Points

* Default methods solve backward compatibility problem.
* Static methods are not inherited.
* Diamond problem must be resolved explicitly.
* Class implementation always takes priority over interface default.

---