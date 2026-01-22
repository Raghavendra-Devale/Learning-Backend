
# Lesson 5: Object Creation & Object Lifecycle

This note explains **how objects are created in Java**, what actually happens when the `new` keyword is used, and how objects move through their lifecycle until they become eligible for garbage collection.

---

## 1. What Happens When We Use `new`

```java
User u = new User();
````

This single line triggers multiple JVM-level steps.
The `new` keyword does **not** directly create an object — it **requests the JVM** to do so.

---

## 2. Step-by-Step Object Creation Process

### Step 1: Class Loading (If Not Already Loaded)

* JVM checks whether the `User` class is loaded
* If not:

  * Class is loaded by ClassLoader
  * Class metadata is stored in **Method Area (Metaspace)**
  * Static variables are initialized

This happens **only once per class**.

---

### Step 2: Memory Allocation

* JVM allocates memory in the **heap**
* Memory size depends on:

  * Instance variables
  * Object header (GC info, JVM metadata)

---

### Step 3: Default Initialization

Before the constructor runs, JVM assigns default values:

* `int` → `0`
* `boolean` → `false`
* Object references → `null`

---

### Step 4: Constructor Execution

```java
User() {
    this.age = 25;
}
```

* Constructor initializes object state
* Constructor **does not allocate memory**
* It only sets values

---

### Step 5: Reference Assignment

* Reference variable stores the address of the object
* Reference location depends on where it is declared:

  * Local variable → stack
  * Instance variable → heap

---

## 3. Object Memory Layout

An object stored in heap contains:

* Object header
* Instance variables

Important:

* **Methods are NOT stored inside objects**
* Method bytecode lives in **Method Area (Metaspace)**

---

## 4. Multiple Objects, Single Class

```java
User u1 = new User();
User u2 = new User();
```

* Two objects created in heap
* Only one class metadata in Metaspace

This explains why:

* Static variables are shared
* Instance variables are not

---

## 5. Object Lifecycle

An object goes through the following states:

1. Created
2. Reachable
3. Unreachable
4. Eligible for Garbage Collection
5. Collected (when GC runs)

---

## 6. Garbage Collection Eligibility

An object becomes eligible for GC when it is **no longer reachable** from any live thread.

Examples:

```java
User u = new User();
u = null;
```

```java
new User(); // no reference
```

```java
User u1 = new User();
User u2 = u1;
u1 = null; // still reachable
```

GC depends on **reachability**, not scope.

---

## 7. Backend Relevance

* Excessive object creation increases GC pressure
* Memory leaks occur when objects remain reachable unintentionally
* Object avoids GC if referenced from static fields or long-lived objects

Understanding object lifecycle is critical for:

* Performance tuning
* Memory leak debugging
* Backend system stability


