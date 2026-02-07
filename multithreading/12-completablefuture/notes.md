# Multithreading – Lesson 12  
## CompletableFuture & Async Programming

These notes explain why CompletableFuture was introduced, how it enables non-blocking async programming, and how to use it correctly in backend systems.

---

## 1. Why CompletableFuture Was Introduced

The older `Future` API had limitations:
- `get()` blocks the calling thread
- No easy way to chain async operations
- Poor exception handling
- Hard to combine multiple async tasks

CompletableFuture was introduced to:
- Enable non-blocking async programming
- Improve readability and composition
- Support complex async workflows

---

## 2. Blocking vs Non-Blocking

### Blocking
- The thread waits until the task completes
- Holds resources unnecessarily
- Limits scalability

### Non-Blocking
- The thread continues execution
- Callback or continuation runs later
- Better throughput and responsiveness

CompletableFuture is designed for non-blocking pipelines.

---

## 3. Creating CompletableFuture

- `supplyAsync()` → runs async and returns a value
- `runAsync()` → runs async without returning a value

By default, tasks run on ForkJoinPool, or a custom Executor can be provided.

---

## 4. thenApply vs thenCompose (Very Important)

### thenApply
- Transforms the result
- Used when the function returns a value
- Comparable to `map()`

### thenCompose
- Flattens nested futures
- Used when the function returns another CompletableFuture
- Comparable to `flatMap()`

Golden rule:
- Value → thenApply
- CompletableFuture → thenCompose

---

## 5. Combining Multiple Futures

- `allOf()` → waits for all tasks to complete
- `anyOf()` → completes when the first task completes

Used for:
- Parallel service calls
- Aggregation APIs
- Concurrent IO operations

---

## 6. Exception Handling in CompletableFuture

Async exceptions do not propagate automatically.

Common methods:
- `exceptionally()`
- `handle()`

Explicit error handling is required in async pipelines.

---

## 7. join() vs get()

- `get()` throws checked exceptions
- `join()` throws unchecked exceptions

Both block the calling thread.

In backend request threads, blocking should be avoided.

---

## 8. Backend Best Practices

- Prefer async chaining over blocking
- Avoid join()/get() in request threads
- Use custom Executor when needed
- Handle exceptions explicitly

---

## 9. Backend Use Cases

CompletableFuture is used in:
- Async REST calls
- Parallel database queries
- Aggregation services
- Non-blocking processing pipelines

---

## 10. Interview-Safe Summary

> “CompletableFuture enables non-blocking async programming with composable pipelines, improving scalability and readability in backend systems.”

---
