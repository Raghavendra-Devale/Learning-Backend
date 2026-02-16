
# 🎯 Java Object Class — Interview Questions & Tricky Scenarios

Goal of this section:

* Understand equality vs identity
* Predict HashMap behavior
* Avoid classic fresher mistakes
* Handle interviewer trap questions confidently

---

## ✅ Level 1 — Direct Interview Questions

---

### 1. Why does every class in Java extend Object?

Because Object provides common functionality required by all objects:

* equality comparison
* hashing
* string representation
* runtime class information

This allows Java APIs to work with any object type.

---

### 2. What is the purpose of `equals()`?

To compare **logical equality** (data equality) between two objects.

Default implementation compares memory references.

---

### 3. What is `hashCode()` used for?

It generates an integer used by hash-based collections like:

* HashMap
* HashSet
* Hashtable

It helps determine bucket location.

---

### 4. Difference between `==` and `equals()`?

| Operator   | Meaning              |
| ---------- | -------------------- |
| `==`       | reference comparison |
| `equals()` | content comparison   |

---

### 5. Why override `toString()`?

To provide meaningful object representation for:

* debugging
* logging
* monitoring

---

## 🧠 Level 2 — Conceptual Understanding

---

### 6. How does HashMap use equals and hashCode?

Process:

```
1. hashCode() → find bucket
2. equals() → find exact object inside bucket
```

Both are required.

---

### 7. What happens if you override equals() but not hashCode()?

HashMap retrieval fails.

Because objects go into different buckets.

This is one of the most common Java bugs.

---

### 8. Can two objects have same hashCode?

Yes.

This is called a **hash collision**.

Then equals() decides actual equality.

---

### 9. Can unequal objects have same hashCode?

Yes.

HashCode is not guaranteed unique.

---

### 10. If two objects are equal, must hashCodes be equal?

✅ YES — mandatory rule.

---

## ⚠️ Level 3 — Classic Interview Traps

---

### 11. Predict Output

```java
class Student {
    String name;
    Student(String name){ this.name = name; }
}

Student s1 = new Student("A");
Student s2 = new Student("A");

System.out.println(s1.equals(s2));
```

✅ Output:

```
false
```

Because equals() not overridden.

---

### 12. HashMap Trap

```java
Map<Student, String> map = new HashMap<>();

Student s1 = new Student("A");
Student s2 = new Student("A");

map.put(s1, "Data");

System.out.println(map.get(s2));
```

✅ Output:

```
null
```

Even though data looks same.

Reason:

Different hashCode + equals comparison fails.

---

### 13. After Proper Override

If equals & hashCode overridden correctly:

```
map.get(s2) → "Data"
```

Now logical equality works.

---

### 14. equals Without Type Check (Common Mistake)

Wrong:

```java
public boolean equals(Object obj){
    Student other = (Student) obj;
    return name.equals(other.name);
}
```

Problem:

Throws `ClassCastException`.

Correct approach includes:

```
instance check + null check
```

---

### 15. Predict Output

```java
String a = new String("Java");
String b = new String("Java");

System.out.println(a.equals(b));
```

✅ true

Because String overrides equals().

---

## 🧩 Level 4 — Deep Interview Questions

---

### 16. Why does HashSet not allow duplicates?

Internally uses HashMap.

Duplicate detection logic:

```
hashCode → equals → reject duplicate
```

---

### 17. Why is equals() argument type Object, not class type?

Polymorphism.

Allows comparison between any objects.

---

### 18. What happens if hashCode always returns same value?

Example:

```java
public int hashCode() {
    return 1;
}
```

Program still works correctly.

BUT performance degrades to O(n).

HashMap becomes like LinkedList.

---

### 19. Which method runs first in HashMap: equals or hashCode?

✅ hashCode first.

equals only runs when bucket matches.

---

### 20. Is overriding hashCode mandatory?

Only if equals is overridden.

Rule:

```
override equals → MUST override hashCode
```

---

## 🧪 Ultimate Interview Brain Teaser

Predict:

```java
Set<Student> set = new HashSet<>();

set.add(new Student("A"));
set.add(new Student("A"));

System.out.println(set.size());
```

Without overriding equals/hashCode:

✅ Output:

```
2
```

With proper override:

✅ Output:

```
1
```

---

## 🧠 Interviewer’s Hidden Goal

They are not testing syntax.

They want to know:

> Do you understand how Java collections internally locate objects?

If you understand Object class contracts, collections stop being memorized APIs and become predictable systems.

---
