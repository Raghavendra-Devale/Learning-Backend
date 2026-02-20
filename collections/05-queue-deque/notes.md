
# Lesson 13: Queue & Deque in Java

This note explains Java `Queue` and `Deque` concepts, focusing on `ArrayDeque` vs `LinkedList`, performance characteristics, and interview-relevant behavior.

---

## 1. Queue Basics

A **Queue** follows **FIFO (First In, First Out)** ordering.

Common backend use cases:

* Request processing
* Task scheduling
* Message handling
* Producer–consumer workflows

---

## 2. Queue Methods

Java provides two styles of queue operations.

### Exception-Based Methods

* `add(E e)` – inserts element, throws exception if capacity restrictions prevent insertion
* `remove()` – removes head, throws exception if queue is empty
* `element()` – retrieves head without removing, throws exception if empty

### Safe Methods (Preferred)

* `offer(E e)` – inserts element, returns `false` if insertion fails
* `poll()` – removes and returns head, returns `null` if empty
* `peek()` – retrieves head without removing, returns `null` if empty

Safe methods are preferred in backend systems because they avoid exceptions during normal control flow.

---

## 3. Deque (Double-Ended Queue)

A `Deque` allows insertion and removal from **both ends**.

It can function as:

* A queue (FIFO)
* A stack (LIFO)
* A sliding window structure

Common operations:

* `addFirst()`, `addLast()`
* `offerFirst()`, `offerLast()`
* `pollFirst()`, `pollLast()`
* `peekFirst()`, `peekLast()`

---

## 4. ArrayDeque

### Internal Working

`ArrayDeque` is implemented using a **resizable circular array**.

* Maintains head and tail indices
* Uses wrap-around indexing
* Avoids element shifting

### Properties

* O(1) insertion and removal at both ends
* Low memory overhead
* Excellent cache locality
* Does **not** allow `null` elements
* Faster iteration compared to linked structures

---

## 5. LinkedList as Queue

`LinkedList` implements both `Queue` and `Deque`.

Characteristics:

* Uses a doubly linked list
* Each node stores references to previous and next elements
* Higher memory overhead
* Poor cache locality
* Slower iteration compared to array-based structures

---

## 6. ArrayDeque vs LinkedList

| Aspect                | ArrayDeque     | LinkedList          |
| --------------------- | -------------- | ------------------- |
| Internal structure    | Circular array | Doubly linked list  |
| Memory overhead       | Low            | High                |
| Cache locality        | Excellent      | Poor                |
| Iteration performance | Faster         | Slower              |
| Null elements         | Not allowed    | Allowed             |
| Typical performance   | Better         | Worse in most cases |

In most backend scenarios, `ArrayDeque` is preferred.

---

## 7. Stack Using Deque

The legacy `Stack` class is discouraged.

Preferred approach:

```java
Deque<Integer> stack = new ArrayDeque<>();
stack.push(1);
stack.pop();
```

Reasons:

* Better performance
* Avoids legacy synchronization overhead
* Cleaner and more modern API design

---

## 8. Backend Usage

Typical applications:

* Request queues
* Task execution pipelines
* Breadth-first search (BFS)
* Depth-first search (DFS)
* Sliding window algorithms
* Undo/redo mechanisms

---

## Key Concepts Summary

* `offer()`, `poll()`, `peek()` are safer alternatives to exception-based methods.
* `ArrayDeque` uses a circular array and provides high performance.
* `LinkedList` has higher memory overhead and weaker cache performance.
* `Deque` is the preferred modern replacement for stack and queue implementations.
* Legacy `Stack` should generally be avoided.

---
