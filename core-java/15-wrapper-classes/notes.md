
# 📘 Wrapper Classes & Autoboxing — Complete Notes

---

## 1. What Are Wrapper Classes?

Java provides object versions of primitive data types.

| Primitive | Wrapper Class |
| --------- | ------------- |
| byte      | Byte          |
| short     | Short         |
| int       | Integer       |
| long      | Long          |
| float     | Float         |
| double    | Double        |
| char      | Character     |
| boolean   | Boolean       |

Example:

```java
int a = 10;          // primitive
Integer b = 10;      // object
```

Wrapper classes live in `java.lang` package.

---

## 2. Why Wrapper Classes Exist

Collections store **objects only**, not primitives.

This is invalid:

```java
List<int> list;   // ❌ not allowed
```

Correct:

```java
List<Integer> list; // ✅
```

Wrapper classes allow primitives to behave like objects.

---

## 3. Autoboxing

### Definition

Automatic conversion of primitive → wrapper object.

Example:

```java
Integer a = 10;
```

Compiler converts it to:

```java
Integer a = Integer.valueOf(10);
```

No manual object creation needed.

---

## 4. Unboxing

Automatic conversion of wrapper → primitive.

```java
Integer a = 10;
int b = a;
```

Compiler converts:

```java
int b = a.intValue();
```

---

## 5. Integer Caching (VERY IMPORTANT)

Java caches Integer objects for values:

```
-128 to 127
```

This is done for performance optimization.

---

### Example

```java
Integer a = 100;
Integer b = 100;

System.out.println(a == b);
```

✅ Output:

```
true
```

Because both references point to cached object.

---

### Outside Cache Range

```java
Integer a = 200;
Integer b = 200;

System.out.println(a == b);
```

✅ Output:

```
false
```

New objects created.

---

### Mental Model

```
Integer Cache:
-128 ... 127 (pre-created objects)
```

JVM reuses them.

---

## 6. `==` vs `equals()` with Wrappers

### `==`

Compares references (object memory).

### `equals()`

Compares values.

Example:

```java
Integer a = 200;
Integer b = 200;

a == b        // false
a.equals(b)   // true
```

Always prefer `equals()`.

---

## 7. Hidden NullPointerException (VERY COMMON BUG)

Unboxing can cause runtime crash.

Example:

```java
Integer a = null;
int b = a;
```

Runtime:

```
NullPointerException
```

Because JVM tries:

```java
a.intValue();
```

on null reference.

---

## 8. Wrapper Classes Are Immutable

Like String:

```java
Integer a = 10;
a = a + 1;
```

Creates new object.

Original object unchanged.

---

## 9. Performance Cost of Autoboxing

Primitive operations are faster.

Example:

```java
int sum = 0;
for(int i=0;i<100000;i++){
    sum += i;
}
```

vs

```java
Integer sum = 0;
```

Second version creates many objects → slower.

Backend systems avoid unnecessary boxing in performance-critical code.

---

## 10. Comparing Primitive and Wrapper

```java
Integer a = 10;
int b = 10;

System.out.println(a == b);
```

✅ Output:

```
true
```

Why?

Wrapper gets unboxed before comparison.

---

## 11. Common Wrapper Utility Methods

```java
Integer.parseInt("10");   // String → primitive
Integer.valueOf("10");    // String → Integer
```

Difference:

* `parseInt()` → returns primitive
* `valueOf()` → returns wrapper

---

## 12. Why `valueOf()` Preferred Over `new Integer()`

```java
Integer a = Integer.valueOf(10);
```

Uses cache when possible.

```java
new Integer(10);
```

Always creates new object (deprecated usage).

---

## 13. Real Backend Usage

Wrappers appear everywhere:

* database values
* JSON mapping
* Optional fields
* collections
* REST APIs

Important reason:

Wrappers can hold **null**, primitives cannot.

Example:

```java
Integer age; // null allowed
int age;     // must have value
```

---

## 🧠 Mental Model

Think:

```
Primitive → raw value
Wrapper   → object container holding value
```

Wrapper adds object behavior but costs memory and performance.

---

## 14. Common Production Bug

```java
Integer count = null;

if(count == 0){
   // crash happens before comparison
}
```

Unboxing happens first → NullPointerException.

---

## ✅ Mastery Checklist

You understand wrappers when you can explain:

* why collections need wrappers
* autoboxing/unboxing process
* Integer cache behavior
* why `Integer == Integer` sometimes true
* null unboxing crash

---
