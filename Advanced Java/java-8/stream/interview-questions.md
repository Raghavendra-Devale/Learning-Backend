---

# ✅ Java Streams — Interview Questions (0–3 YOE)

---

# 🔹 0 Level

---

### 1️⃣ What is a Stream?

A Stream is a sequence of elements that supports functional-style operations for processing data declaratively.

It allows operations like filtering, mapping, sorting, and aggregation using a pipeline model.

Keywords to mention:

* Declarative style
* Functional programming
* Pipeline

---

### 2️⃣ Is Stream a data structure?

No.

A Stream is not a data structure because it does not store data. It processes data from a source like a Collection, array, or I/O channel.

---

### 3️⃣ What is lazy evaluation?

Lazy evaluation means intermediate operations are not executed until a terminal operation is invoked.

This improves performance and enables short-circuiting.

---

### 4️⃣ What are intermediate operations?

Intermediate operations:

* Return a Stream
* Are lazy
* Build the pipeline

Examples:

* filter
* map
* flatMap
* sorted
* distinct

---

### 5️⃣ What are terminal operations?

Terminal operations:

* Trigger execution
* Produce a result

Examples:

* collect
* toList
* count
* reduce
* findFirst

---

# 🔹 Fresher Level

---

### 1️⃣ Difference between map and filter?

filter removes elements based on a condition.

map transforms each element into another element.

Example:

* filter → removes inactive users
* map → extracts email from user

---

### 2️⃣ Difference between map and flatMap?

map:
1 element → 1 element

flatMap:
1 element → multiple elements → flattened

Use flatMap when working with nested collections.

---

### 3️⃣ Why is Stream single-use?

Streams represent a pipeline of operations. After a terminal operation executes, the stream is consumed and cannot be reused.

Reusing it throws IllegalStateException.

---

### 4️⃣ What happens without terminal operation?

Nothing executes.

Because streams are lazy, intermediate operations alone do not trigger execution.

---

### 5️⃣ What are short-circuit operations?

Operations that may stop processing early when a condition is met.

Examples:

* findFirst
* findAny
* anyMatch
* limit

---

# 🔹 1–2 YOE

---

### 1️⃣ What is internal iteration?

Internal iteration means the Stream API controls how elements are iterated internally, unlike external iteration where the developer uses loops.

---

### 2️⃣ Explain groupingBy with example.

groupingBy groups elements based on a classifier function.

Example:

Group users by department:

```java
.collect(Collectors.groupingBy(User::getDepartment));
```

Returns:
Map<Department, List<User>>

---

### 3️⃣ What happens if duplicate keys in toMap?

If duplicate keys exist and no merge function is provided, toMap throws IllegalStateException.

To handle it:

```java
.toMap(
    User::getEmail,
    Function.identity(),
    (existing, replacement) -> existing
)
```

---

### 4️⃣ Difference between groupingBy and partitioningBy?

groupingBy:

* Can create multiple groups
* Key can be any type

partitioningBy:

* Only splits into true/false
* Always returns Map<Boolean, List<T>>

---

### 5️⃣ Why avoid side effects in streams?

Side effects can cause unpredictable behavior, especially in parallel streams.

Streams should use stateless and non-interfering operations.

---

### 6️⃣ What is stateful vs stateless operation?

Stateless:
Does not depend on other elements.
Example: map, filter

Stateful:
Needs to process entire stream.
Example: sorted, distinct

Stateful operations may require buffering.

---

### 7️⃣ Difference between findFirst and findAny?

findFirst:
Returns first element based on encounter order.

findAny:
Returns any element. More efficient in parallel streams.

---

# 🔹 2–3 YOE

---

### 1️⃣ When should you avoid streams?

Avoid streams when:

* Logic is very simple (loop is clearer)
* Heavy mutation required
* Debugging becomes complex
* Performance-critical tight loops
* I/O-heavy operations

---

### 2️⃣ Is stream always faster than loop?

No.

Streams add abstraction overhead.
For small collections, loops may be faster.

Parallel streams may improve performance for large CPU-bound datasets.

---

### 3️⃣ What happens if source collection is modified during streaming?

It can cause ConcurrentModificationException.

Streams require non-interference — the source should not be modified while processing.

---

### 4️⃣ Explain parallelStream.

parallelStream processes elements in parallel using ForkJoinPool.commonPool().

It divides data into chunks and processes them across multiple threads.

---

### 5️⃣ Why is parallelStream risky in Spring Boot?

Because:

* It uses common ForkJoinPool
* May interfere with request threads
* Not suitable for blocking I/O
* Can exhaust thread pool

It’s risky in web applications.

---

### 6️⃣ Why does maxBy return Optional?

Because the stream might be empty.

To avoid returning null, it returns Optional to enforce safe handling.

---

# 🔥 Additional Interview Questions (Must Know)

---

### 1️⃣ Difference between Stream and Collection?

Collection stores data.

Stream processes data.

Collection is reusable.

Stream is single-use.

---

### 2️⃣ What is encounter order?

The order in which elements appear in the source.

Some operations preserve it, some don’t.

---

### 3️⃣ What is non-interference?

Operations should not modify the source while it is being processed.

---

### 4️⃣ What is reduce?

reduce performs immutable reduction by combining elements into a single result.

Example:

```java
.reduce(0, Integer::sum);
```

---

### 5️⃣ Why is collect preferred over reduce for Lists?

collect is designed for mutable containers.

reduce is meant for immutable reduction.

---

### 6️⃣ What is peek used for?

peek is mainly for debugging and should not be used for modifying elements.

---

### 7️⃣ Are Streams thread-safe?

Streams themselves are not thread-safe.

Parallel streams require stateless and non-interfering operations.

---

### 8️⃣ What is boxing overhead in streams?

Using Stream<Integer> causes boxing and unboxing.

Primitive streams like IntStream avoid this overhead.

---