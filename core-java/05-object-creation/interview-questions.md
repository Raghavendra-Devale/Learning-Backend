
## 🎯 `interview-questions.md` — Lesson 5

```md
# Interview Questions – Object Creation & Lifecycle

---

## Q1. What happens internally when we create an object using `new`?

### Answer:
When `new` is used, the JVM loads the class if required, allocates memory in heap, initializes default values, executes the constructor, and returns a reference to the object.

---

## Q2. Does the constructor allocate memory?

### Answer:
No. Memory is allocated by the JVM before the constructor runs. The constructor only initializes the object.

---

## Q3. Where are objects stored in Java?

### Answer:
Objects are stored in heap memory.

---

## Q4. Where are methods stored?

### Answer:
Method bytecode is stored in the Method Area (Metaspace), not inside objects.

---

## Q5. When does an object become eligible for garbage collection?

### Answer:
An object becomes eligible for garbage collection when it is no longer reachable from any live thread.

---

## Q6. Does garbage collection run immediately after an object becomes unreachable?

### Answer:
No. Garbage collection runs when the JVM decides, not immediately after an object becomes unreachable.

---

## Q7. Can an object exist without any reference?

### Answer:
Yes. An object can exist without references, but it becomes immediately eligible for garbage collection.

---

## Q8. What causes memory leaks in Java?

### Answer:
Memory leaks occur when objects remain reachable unintentionally, such as through static references or long-lived objects.

---

## Common Interview Traps & Pitfalls

❌ Saying constructor allocates memory  
❌ Saying objects are destroyed immediately when references are removed  
❌ Confusing reachability with variable scope  
❌ Saying methods are stored in heap  

---

## One Interview-Safe Explanation

> “When `new` is used, the JVM allocates memory in heap, initializes default values, executes the constructor, and returns a reference. Objects become eligible for garbage collection when they are no longer reachable.”

