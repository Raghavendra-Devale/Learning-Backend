
# 📘 Java Strings — Complete Notes

## 1. What is a String in Java?

A `String` in Java is an **object** representing a sequence of characters.

```java
String name = "Raghu";
```

Even though it looks like a primitive, it is actually:

```java
String name = new String("Raghu");
```

under the hood (with important optimizations).

Key idea:

> String is a special class treated differently by the JVM for performance and memory efficiency.

---

## 2. Why String is Special in Java

Strings are used everywhere:

* API requests & responses
* Database queries
* File paths
* JSON/XML
* Logging
* Security tokens

Because of heavy usage, Java introduced special optimizations:

* String Constant Pool
* Immutability
* Compiler optimizations

---

## 3. String Immutability (VERY IMPORTANT)

### Definition

A String object **cannot be changed after creation**.

Example:

```java
String s = "Hello";
s.concat(" World");
System.out.println(s);
```

Output:

```
Hello
```

Why?

Because `concat()` creates a **new object**, not modify existing one.

---

### Internal Behavior

```
Before:
s → "Hello"

After concat:
s → "Hello"
new object → "Hello World"
```

Original string remains unchanged.

---

### Why Java Made Strings Immutable

#### ✅ 1. Security

Used in:

* class loading
* file paths
* database connections

If mutable, attackers could modify references.

---

#### ✅ 2. String Pool Optimization

Multiple variables can safely share same object.

---

#### ✅ 3. Thread Safety

Immutable objects are automatically thread-safe.

No synchronization required.

---

#### ✅ 4. HashCode Caching

String hashCode is cached once computed.

Important for HashMap performance.

---

## 4. String Constant Pool (SCP)

The JVM maintains a special memory area inside heap called:

> **String Constant Pool**

It stores unique string literals.

---

### Example

```java
String a = "Java";
String b = "Java";
```

Memory:

```
String Pool:
   "Java"

a ─┐
   └──> "Java"
b ─┘
```

Both references point to SAME object.

---

### Using `new` Keyword

```java
String a = new String("Java");
```

Now JVM creates:

* one object in pool
* one object in heap

```
Heap Object → "Java"
Pool Object → "Java"
```

Two objects exist.

---

## 5. `==` vs `equals()` (Classic Interview Trap)

### `==`

Compares **memory reference**

### `equals()`

Compares **content**

Example:

```java
String a = "Java";
String b = "Java";
System.out.println(a == b); // true
```

Because both refer same pooled object.

---

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a == b);      // false
System.out.println(a.equals(b)); // true
```

---

Rule:

> Always use `equals()` for string comparison.

---

## 6. String Creation Ways

### Method 1 — Literal (Recommended)

```java
String s = "Hello";
```

Uses String Pool.

Memory efficient.

---

### Method 2 — Using `new`

```java
String s = new String("Hello");
```

Creates extra object.

Rarely needed.

---

## 7. String Interning

Interning forces JVM to use pool reference.

```java
String s1 = new String("Java");
String s2 = s1.intern();
```

Now `s2` refers to pooled object.

Used for memory optimization.

---

## 8. StringBuilder vs StringBuffer

Since String is immutable:

This is inefficient:

```java
String s = "";
for(int i=0;i<1000;i++){
    s += i;
}
```

Creates 1000 objects.

---

### StringBuilder (Preferred)

Mutable and fast.

```java
StringBuilder sb = new StringBuilder();
sb.append("Hello");
```

✅ Not thread-safe
✅ Faster

Used in most backend applications.

---

### StringBuffer

Same as StringBuilder but:

✅ Thread-safe (synchronized)
❌ Slower

Used in multi-threaded legacy scenarios.

---

### Comparison

| Feature     | String              | StringBuilder | StringBuffer |
| ----------- | ------------------- | ------------- | ------------ |
| Mutable     | ❌                   | ✅             | ✅            |
| Thread Safe | ✅                   | ❌             | ✅            |
| Performance | Slow (modification) | Fast          | Medium       |

---

## 9. Compiler Optimization

Java converts:

```java
String s = a + b;
```

into:

```java
new StringBuilder().append(a).append(b).toString();
```

at compile time.

Meaning:

`+` is safe for small operations but not loops.

---

## 10. Memory Efficiency Example

```java
String s1 = "Hello";
String s2 = "Hello";
String s3 = "Hello";
```

Only ONE object exists in pool.

Huge memory savings in real systems.

---

## 11. Important Interview Concepts

### Strings are:

* Immutable
* Final class
* Serializable
* Comparable

---

### Why String class is final?

Prevents modification of behavior → ensures security & immutability.

---

## 12. Real Backend Usage Insight

Strings appear everywhere:

* REST APIs
* JSON parsing
* HTTP headers
* Query construction

Using StringBuilder in loops prevents memory overhead and improves performance under load.

---

## 🧠 Mental Model to Remember

Think of String as:

> A read-only shared object optimized by JVM for safety and reuse.

While:

```
StringBuilder = editable notebook
String = printed book
```

You can write freely in notebook, but printed book never changes.

---
