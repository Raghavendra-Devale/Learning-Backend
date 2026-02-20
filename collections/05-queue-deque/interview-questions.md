# Interview Questions – Queue & Deque

---

## Q1. Difference between add() and offer() in Queue?
**Answer:**  
`add()` throws an exception if the queue cannot accept more elements, while `offer()` returns `false`.  
`offer()` is preferred in backend systems because it avoids exceptions during normal control flow.

---

## Q2. Difference between poll() and remove()?
**Answer:**  
`poll()` removes and returns the head of the queue or returns `null` if the queue is empty, while `remove()` throws an exception when the queue is empty.

---

## Q3. What is Deque?
**Answer:**  
`Deque` (Double-Ended Queue) is a data structure that allows insertion and removal of elements from both ends.

---

## Q4. Why is ArrayDeque preferred over LinkedList?
**Answer:**  
`ArrayDeque` has lower memory overhead, better cache locality, and higher performance due to its circular array implementation.

---

## Q5. Why does ArrayDeque not allow null?
**Answer:**  
To avoid ambiguity between an empty queue and a queue containing `null` during `peek()` or `poll()` operations.

---

## Q6. Why is Stack class discouraged?
**Answer:**  
`Stack` is a legacy synchronized class with unnecessary overhead. `Deque` implementations provide a faster and cleaner alternative.

---

## Q7. Can ArrayDeque be used as a stack?
**Answer:**  
Yes. `ArrayDeque` supports `push()` and `pop()` operations and is preferred over `Stack`.

---

## Common Interview Traps & Pitfalls

❌ Saying LinkedList is the best queue  
❌ Using add/remove blindly  
❌ Saying Stack is recommended  
❌ Forgetting null restriction

---

## One Interview-Safe Explanation

> Queue models FIFO behavior, while Deque supports insertion and removal from both ends. ArrayDeque is preferred over LinkedList for queue and stack use cases due to better performance and lower memory overhead.

---