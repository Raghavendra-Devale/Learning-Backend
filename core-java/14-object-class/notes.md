
# 📘 Java Object Class — Complete Notes

---

## 1. What is the Object Class?

In Java:

> Every class directly or indirectly extends `java.lang.Object`.

Example:

```java
class Student {
}
```

Internally becomes:

```java
class Student extends Object {
}
```

This means every object automatically gets common behavior defined by the Object class.

---

## 2. Why Object Class Exists

Java needed a universal parent so all objects share common capabilities:

* comparison
* hashing
* string representation
* runtime type information
* synchronization support

This allows Java APIs (Collections, logging, frameworks) to work with **any object**.

---

## 3. Important Methods of Object Class

The most important ones for backend and interviews:

* `toString()`
* `equals(Object obj)`
* `hashCode()`
* `getClass()`
* `clone()` (basic awareness)
* `wait(), notify(), notifyAll()` (threading connection)

We focus mainly on the first three.

---

## 4. `toString()` Method

### Default Behavior

```java
Object obj = new Object();
System.out.println(obj);
```

Output:

```
java.lang.Object@1b6d3586
```

Format:

```
ClassName@HexadecimalHashCode
```

Not useful for debugging.

---

### Overriding toString()

```java
class Student {
    String name;

    public String toString() {
        return "Student name = " + name;
    }
}
```

Now printing object gives meaningful information.

---

### Why Important?

Used automatically in:

* logging
* debugging
* API responses
* monitoring tools

Good engineers override `toString()`.

---

## 5. `equals()` Method

### Default Implementation

Default `equals()` compares memory addresses.

Equivalent to:

```java
return this == obj;
```

Example:

```java
Student s1 = new Student("A");
Student s2 = new Student("A");

System.out.println(s1.equals(s2));
```

Output:

```
false
```

Even though data is same.

---

### Why Override equals()?

Because logical equality ≠ memory equality.

We usually want:

> Two objects are equal if their data is equal.

---

### Correct equals() Implementation

```java
@Override
public boolean equals(Object obj) {

    if (this == obj)
        return true;

    if (obj == null || getClass() != obj.getClass())
        return false;

    Student other = (Student) obj;

    return this.name.equals(other.name);
}
```

---

## 6. `hashCode()` Method

Returns an integer representing object’s hash value.

Used heavily in:

* HashMap
* HashSet
* HashTable

---

### Default Behavior

Each object gets different hash code based on memory.

---

### Why hashCode Exists

Hash-based collections use hashCode to decide **bucket location**.

Process inside HashMap:

```
hashCode() → bucket selection
equals()   → object comparison inside bucket
```

Both methods work together.

---

## 7. equals() and hashCode() Contract (VERY IMPORTANT)

Rule 1:

If two objects are equal using `equals()`:

```
their hashCode MUST be same.
```

Rule 2:

If hashCodes are same, objects MAY or MAY NOT be equal.

---

### What Happens If Contract Breaks?

HashMap fails to retrieve object.

Example problem:

```java
map.put(student1, "Data");
map.get(student2);
```

Even if logically equal → retrieval fails.

This is a classic interview scenario.

---

## 8. Correct hashCode Implementation

Typical pattern:

```java
@Override
public int hashCode() {
    return name.hashCode();
}
```

Modern approach:

```java
@Override
public int hashCode() {
    return Objects.hash(name);
}
```

---

## 9. equals() vs `==`

| Feature             | equals() | ==        |
| ------------------- | -------- | --------- |
| Comparison          | Content  | Reference |
| Overridable         | Yes      | No        |
| Used in Collections | Yes      | No        |

---

## 10. `getClass()` Method

Returns runtime class information.

```java
obj.getClass()
```

Used in:

* reflection
* frameworks
* runtime inspection

Spring internally relies on this concept.

---

## 11. Object Creation Lifecycle (Conceptual)

When object is created:

```
1. Memory allocated in heap
2. Constructor executed
3. Object reference returned
4. Object methods available
```

All objects inherit Object behavior automatically.

---

## 12. Why This Topic Matters in Backend

Collections rely heavily on Object rules:

* HashMap keys
* caching systems
* entity comparison
* deduplication logic

Incorrect equals/hashCode causes production bugs that are extremely hard to detect.

---

## 🧠 Mental Model

Think of:

```
hashCode() → house number
equals()   → person identity check
```

Mail delivery:

1. Go to house (hashCode)
2. Verify person (equals)

If house number wrong → mail never arrives.

---

## 13. Common Real-World Bug

Developer overrides equals but not hashCode.

Result:

* HashSet stores duplicates
* HashMap retrieval fails
* caching behaves unpredictably

This is one of the most famous Java mistakes.

---

## ✅ Mastery Checklist

You understand Object class when you can explain:

* why every class extends Object
* difference between identity and equality
* why HashMap needs both equals and hashCode
* how overriding affects collections

---
