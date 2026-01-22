## 🎯 `interview-questions.md` — Lesson 6

```md
# Interview Questions – Garbage Collection (GC)

---

## Q1. What is Garbage Collection in Java?

### Answer:
Garbage Collection is a JVM process that automatically reclaims heap memory by removing objects that are no longer reachable.

---

## Q2. How does JVM decide which objects to collect?

### Answer:
JVM uses reachability analysis. Objects not reachable from any GC root are eligible for garbage collection.

---

## Q3. What are GC roots?

### Answer:
GC roots include active thread stacks, static variables, and JNI references from which object reachability is determined.

---

## Q4. Why does JVM use generational garbage collection?

### Answer:
Because most objects die young, generational GC improves performance by frequently collecting short-lived objects.

---

## Q5. What is Stop-The-World?

### Answer:
Stop-The-World is a phase during garbage collection where all application threads are paused to safely perform GC.

---

## Q6. What is the difference between Minor GC and Full GC?

### Answer:
Minor GC runs on the Young Generation and is fast, while Full GC runs on the Old Generation and is slower with longer pauses.

---

## Q7. Can `System.gc()` force garbage collection?

### Answer:
No. `System.gc()` only requests GC, and the JVM decides whether to run it.

---

## Q8. What causes GC performance issues in backend applications?

### Answer:
Excessive object creation, large objects, static references, and improper caching can increase GC pressure.

---

## Common Interview Traps & Pitfalls

❌ Saying GC runs immediately when object is unreachable  
❌ Saying GC is based on reference counting  
❌ Saying `System.gc()` guarantees GC  
❌ Ignoring Stop-The-World impact  

---

## One Interview-Safe Explanation

> “Garbage Collection in Java automatically reclaims heap memory by removing objects that are no longer reachable. The JVM uses a generational approach to optimize performance while minimizing pause times.”

