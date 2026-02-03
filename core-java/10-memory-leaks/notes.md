# Lesson 18: Java Memory Leaks & Weak References

This note explains how memory leaks occur in Java despite garbage collection, common leak patterns in backend systems, and how weak references help prevent leaks.

---

## 1. Java Memory Leaks – The Truth

Java uses Garbage Collection, but memory leaks can still occur.

A memory leak happens when:
- Objects are **no longer needed**
- But still **reachable**
- So GC cannot reclaim them

Garbage Collection is based on **reachability**, not usefulness.

---

## 2. GC Roots (Important Concept)

Objects are considered reachable if they are referenced from:
- Static variables
- Active threads
- Stack frames
- JNI references

If an object is reachable from a GC Root, it will not be collected.

---

## 3. Static Reference Leaks

```java
class Cache {
    static Map<String, Object> map = new HashMap<>();
}
````

Problem:

* Static variables live for JVM lifetime
* Objects added remain reachable forever unless removed

---

## 4. Collection-Based Leaks

Collections are a common source of leaks.

```java
List<Object> list = new ArrayList<>();
list.add(new Object());
```

If objects are not removed:

* Collection keeps references
* GC cannot reclaim memory

---

## 5. Listener / Callback Leaks

Registering listeners without unregistering them causes leaks.

```java
registerListener(this);
// but never unregisterListener(this)
```

Long-lived objects retain references to short-lived objects.

---

## 6. ThreadLocal Memory Leaks (Very Important)

ThreadLocal leaks occur because:

* Threads in pools are long-lived
* ThreadLocal values remain attached to threads
* Values must be explicitly removed

Correct usage:

```java
try {
    threadLocal.set(value);
} finally {
    threadLocal.remove();
}
```

---

## 7. Weak References

Java provides reference types:

* Strong
* Soft
* Weak
* Phantom

Weak references do not prevent garbage collection.

---

## 8. WeakHashMap

`WeakHashMap` stores keys using weak references.

When a key is no longer strongly referenced:

* Entry is automatically removed

Used for:

* Caches
* Metadata
* Temporary associations

---

## 9. Backend Reality

Most Java memory leaks are caused by:

* Static collections
* Unbounded caches
* ThreadLocal misuse
* Underegistered listeners

Not by missing free() calls.

---

## 10. Interview-Safe Summary

> “Java memory leaks occur when objects remain reachable from GC Roots even though they are no longer needed. Weak references help prevent leaks by allowing garbage collection when no strong references exist.”

---

