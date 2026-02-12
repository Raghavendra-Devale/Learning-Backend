
---

# ✅ Java Streams — Twisted / Trap Questions (With Deep Explanation)

---

### 1️⃣ Will this execute?

```java
list.stream().map(String::toUpperCase);
```

**Answer:**
No.

**Why?**

Because there is no terminal operation.
Streams are lazy. Intermediate operations like `map()` only build the pipeline.
Execution starts only when a terminal operation is invoked.

Interview keyword: **Lazy evaluation**

---

### 2️⃣ What happens here?

```java
Stream<String> s = list.stream();
s.forEach(System.out::println);
s.forEach(System.out::println);
```

**Answer:**
Throws `IllegalStateException`.

**Why?**

Streams are single-use.
Once a terminal operation is executed, the stream is considered consumed and closed.

Interview keyword: **Consumed stream**

---

### 3️⃣ Is this good practice?

```java
List<String> result = new ArrayList<>();
list.stream().forEach(result::add);
```

**Answer:**
It works, but it is not good practice.

**Why?**

* Introduces side effects
* Breaks functional style
* Not safe in parallel streams
* Reduces readability

Better:

```java
List<String> result = list.stream().toList();
```

Interview keyword: **Side effects**

---

### 4️⃣ Why might distinct() fail to remove duplicates?

**Answer:**
If `equals()` and `hashCode()` are not properly overridden.

**Why?**

`distinct()` internally uses a `HashSet`.
Duplicate detection depends on `equals()` and `hashCode()`.

This is a very common trap for custom objects.

---

### 5️⃣ What happens if toMap has duplicate keys and no merge function?

**Answer:**
Throws `IllegalStateException`.

Because `toMap()` cannot resolve duplicate keys unless a merge function is provided.

---

### 6️⃣ Is parallelStream always faster?

**Answer:**
No.

Parallel streams may be slower due to:

* Thread management overhead
* Small datasets
* Synchronization cost
* Blocking operations

Parallel helps only for large CPU-bound workloads.

---

### 7️⃣ Why can limit() stop early?

**Answer:**
Because `limit()` is a short-circuiting intermediate operation.

It stops processing once the required number of elements is reached.

Important: It improves performance in large streams.

---

# 🔥 Additional Twisted Questions (Advanced Traps)

---

### 8️⃣ What happens if you modify the source collection during streaming?

Example:

```java
list.stream().forEach(e -> list.add("new"));
```

**Answer:**
May throw `ConcurrentModificationException`.

Streams require **non-interference** — the source should not be modified during processing.

---

### 9️⃣ What is wrong with this in parallel stream?

```java
int[] sum = {0};
list.parallelStream().forEach(n -> sum[0] += n);
```

**Answer:**
Race condition.

Why?
Because multiple threads update shared mutable state.

Correct approach:

```java
int sum = list.parallelStream().reduce(0, Integer::sum);
```

Interview keyword: **Stateless lambda**

---

### 🔟 Does stream guarantee order?

Depends.

* Sequential stream preserves encounter order.
* Parallel stream may not (unless using forEachOrdered).

---
