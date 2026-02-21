

# 🎯 Wrapper Classes & Autoboxing — Interview Questions

This section focuses on:

* Integer caching traps
* Autoboxing/unboxing behavior
* Hidden NullPointerExceptions
* Performance and comparison pitfalls

Goal:

> Predict JVM behavior instead of guessing outputs.

---

## ✅ Level 1 — Direct Interview Questions

---

### 1. What are wrapper classes?

Object representations of primitive data types that allow primitives to be used where objects are required (like Collections).

Example:

```
int → Integer
char → Character
```

---

### 2. What is autoboxing?

Automatic conversion of primitive to wrapper object.

```java
Integer a = 10;
```

Compiler converts to:

```java
Integer a = Integer.valueOf(10);
```

---

### 3. What is unboxing?

Automatic conversion of wrapper object to primitive.

```java
Integer a = 10;
int b = a;
```

Internally:

```java
int b = a.intValue();
```

---

### 4. Why do collections use wrapper classes?

Collections store objects only, not primitives.

```
List<Integer> ✅
List<int> ❌
```

---

### 5. Are wrapper classes mutable?

No. Wrapper classes are immutable.

---

## 🧠 Level 2 — Conceptual Understanding

---

### 6. What is Integer caching?

JVM caches Integer objects in range:

```
-128 to 127
```

to improve performance and reduce memory usage.

---

### 7. Difference between `parseInt()` and `valueOf()`?

| Method       | Returns        |
| ------------ | -------------- |
| `parseInt()` | primitive int  |
| `valueOf()`  | Integer object |

---

### 8. Why is `valueOf()` preferred over constructor?

`valueOf()` uses cache.

Constructor always creates new object.

---

### 9. Can wrapper objects store null?

Yes.

```java
Integer a = null;
```

Primitive types cannot.

---

## ⚠️ Level 3 — Classic Interview Traps

---

### 10. Predict Output

```java
Integer a = 100;
Integer b = 100;

System.out.println(a == b);
```

✅ Output:

```
true
```

Because values fall inside Integer cache range.

---

### 11. Predict Output

```java
Integer a = 200;
Integer b = 200;

System.out.println(a == b);
```

✅ Output:

```
false
```

Outside cache → new objects created.

---

### 12. equals() vs `==`

```java
Integer a = 200;
Integer b = 200;

System.out.println(a.equals(b));
```

✅ Output:

```
true
```

equals compares values.

---

### 13. Primitive + Wrapper Comparison

```java
Integer a = 10;
int b = 10;

System.out.println(a == b);
```

✅ Output:

```
true
```

Wrapper gets unboxed before comparison.

---

### 14. Hidden NullPointerException

```java
Integer a = null;
int b = a;
```

✅ Runtime:

```
NullPointerException
```

Because JVM performs unboxing:

```
a.intValue()
```

on null reference.

---

### 15. Another Trap

```java
Integer a = null;

if(a == 0){
    System.out.println("Hello");
}
```

Program crashes before comparison.

Unboxing happens first.

---

## 🧩 Level 4 — Deep Interview Questions

---

### 16. Why does Java cache Integer objects?

Because small integers are frequently used.

Reusing objects improves:

* memory usage
* performance

---

### 17. Does caching apply to all wrappers?

Mostly yes for small ranges:

* Integer
* Short
* Byte
* Long (partial)
* Character (0–127)

---

### 18. Which is faster: primitive or wrapper?

Primitive.

Wrappers involve:

* object creation
* heap allocation
* garbage collection

---

### 19. Why wrappers are common in backend APIs?

Because they allow null values.

Example:

```
age = null → value not provided
```

Important for database and JSON mapping.

---

### 20. Predict Output (Brain Teaser)

```java
Integer a = 127;
Integer b = 127;
Integer c = 128;
Integer d = 128;

System.out.println(a == b);
System.out.println(c == d);
```

✅ Output:

```
true
false
```

Cache boundary demonstration.

---

## 🧪 Ultimate Interview Scenario

```java
Integer a = 100;
Integer b = 100;
Integer c = new Integer(100);

System.out.println(a == b);
System.out.println(a == c);
System.out.println(a.equals(c));
```

✅ Output:

```
true
false
true
```

Explanation:

* a & b → cached object
* c → new heap object
* equals compares values

---

## 🧠 Interviewer’s Hidden Goal

They want to see whether you understand:

* object vs primitive behavior
* JVM optimizations
* implicit conversions done by compiler

If you can mentally see boxing/unboxing happening, these questions become trivial.

---

## ✅ Mastery Checklist

You are strong here when you can explain:

* why Integer == Integer behaves inconsistently
* when unboxing occurs automatically
* why null wrappers crash programs
* performance impact of boxing

---
