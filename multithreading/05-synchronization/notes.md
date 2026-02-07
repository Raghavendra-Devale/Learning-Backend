# Multithreading – Lesson 5  
## Synchronization (`synchronized`)

These notes explain why synchronization is required in Java, how `synchronized` works internally, and the guarantees it provides.

---

## 1. Why Synchronization Is Needed

Synchronization is needed to prevent race conditions when:
- Multiple threads access shared data
- At least one thread modifies that data

Without synchronization, data inconsistency occurs.

---

## 2. What `synchronized` Means

When code is marked as `synchronized`:
- Only one thread can execute that code at a time
- Other threads must wait until the lock is released

This ensures mutual exclusion.

---

## 3. Monitor Lock (Intrinsic Lock)

- Every Java object has one monitor lock
- The lock is managed by the JVM
- The lock is not visible in code

Entering a synchronized section acquires the lock.  
Exiting releases it.

---

## 4. Lock Is Associated with Object (Very Important)

Locks are:
- Associated with objects
- NOT associated with code

Threads must compete for the **same object’s lock** to achieve synchronization.

---

## 5. Synchronized Method

```java
public synchronized void increment() {
    count++;
}
````

* Lock is acquired on the current object (`this`)
* Entire method becomes a critical section

---

## 6. Synchronized Block

```java
synchronized(this) {
    count++;
}
```

Advantages:

* Smaller critical section
* Better performance
* More control over locking

Block-level synchronization is generally preferred.

---

## 7. Object-Level Locking

```java
synchronized(this) { }
```

* Lock is on the current object instance
* Threads must use the same instance to synchronize correctly

Different objects → different locks → no synchronization.

---

## 8. Class-Level Locking

```java
public static synchronized void method() { }
```

Equivalent to:

```java
synchronized(ClassName.class) { }
```

* Lock is on the Class object
* Used for static shared data

---

## 9. Guarantees Provided by synchronized

`synchronized` provides:

1. Mutual exclusion
2. Visibility guarantee (changes are visible to other threads)

---

## 10. What synchronized Does NOT Guarantee

* No fairness
* No deadlock prevention
* No performance guarantee
* No ordering across different locks

---

## 11. Backend Reality

* synchronized is not inherently slow
* JVM optimizes locking heavily
* Incorrect locking strategy causes performance issues

---

## 12. Interview-Safe Summary

> “`synchronized` ensures mutual exclusion and visibility using an object’s monitor lock. The lock is associated with an object, not the code.”

---




