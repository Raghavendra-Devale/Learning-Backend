# Lesson 13: Queue & Deque in Java

This note explains Java Queue and Deque concepts, focusing on `ArrayDeque` vs `LinkedList`, performance, and interview-relevant behavior.

---

## 1. Queue Basics

A Queue follows **FIFO (First In, First Out)** ordering.

Common backend use cases:
- Request processing
- Task scheduling
- Message handling

---

## 2. Queue Methods

Java provides two styles of queue operations:

### Exception-based
- add()
- remove()
- element()

### Safe methods (preferred)
- offer()
- poll()
- peek()

`offer()`, `poll()`, and `peek()` are preferred in backend systems because they do not throw exceptions.

---

## 3. Deque (Double Ended Queue)

A `Deque` allows insertion and removal from **both ends**.

It can be used as:
- Queue
- Stack
- Sliding window structure

---

## 4. ArrayDeque

### Internal Working
- Implemented using a **resizable circular array**
- Maintains head and tail indices
- Wrap-around logic for efficiency

### Properties
- O(1) insertion and removal at both ends
- Low memory overhead
- Excellent cache locality
- Does NOT allow `null`

---

## 5. LinkedList as Queue

`LinkedList` can implement Queue and Deque, but:

- Uses a doubly linked list
- Each element stores extra references
- Higher memory overhead
- Poor cache locality

---

## 6. ArrayDeque vs LinkedList

| Aspect | ArrayDeque | LinkedList |
|-----|-----------|-----------|
| Internal DS | Circular array | Doubly linked list |
| Memory overhead | Low | High |
| Cache locality | Excellent | Poor |
| Performance | Faster | Slower |

In real backend systems, `ArrayDeque` is preferred.

---

## 7. Stack Using Deque

The legacy `Stack` class is discouraged.

Preferred approach:
```java
Deque<Integer> stack = new ArrayDeque<>();
stack.push(1);
stack.pop();
````

Reasons:

* Better performance
* No legacy synchronization
* Cleaner API

---

## 8. Backend Usage

* Request queues
* Task execution
* BFS / DFS
* Sliding window problems
* Undo / redo logic

---

---

## 🧠 LOCK THIS MENTAL MODEL

* `offer()` → safe, preferred
* `add()` → exception-based
* `ArrayDeque` → circular array, cache-friendly
* `LinkedList` → node-heavy, slow iteration
* `Stack` → legacy, avoid
* `Deque` → modern stack + queue

You’re solid.

---