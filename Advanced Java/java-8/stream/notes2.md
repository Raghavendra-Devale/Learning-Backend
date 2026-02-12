
# ✅ PART 2 — Advanced + Backend Focus

---

# 1️⃣ Collectors (Very Important)

collect() performs mutable reduction.

---

## Common Collectors

* toList()
* toSet()
* toMap()
* groupingBy()
* partitioningBy()
* counting()
* summingDouble()
* averagingDouble()
* maxBy()
* minBy()

---

# 2️⃣ toMap() Duplicate Key Trap (Very Important)

This throws exception:

```java
.toMap(User::getEmail, Function.identity());
```

If duplicate keys exist → IllegalStateException

---

## Correct Way

```java
.toMap(
    User::getEmail,
    Function.identity(),
    (existing, replacement) -> existing
)
```

Interview line:

Always handle duplicate keys when using toMap.

---

# 3️⃣ groupingBy vs partitioningBy

### groupingBy

Groups by any key.

```java
.groupingBy(User::getDepartment);
```

Returns:
Map<Department, List<User>>

---

### partitioningBy

Splits into true/false.

```java
.partitioningBy(User::isActive);
```

Returns:
Map<Boolean, List<User>>

---

# 4️⃣ Primitive Streams (Performance)

Use:

* IntStream
* LongStream
* DoubleStream

Example:

```java
double total = employees.stream()
                        .mapToDouble(Employee::getSalary)
                        .sum();
```

Avoids boxing overhead.

---

# 5️⃣ Parallel Streams

Use:

```java
.parallelStream()
```

Uses ForkJoinPool.commonPool().

---

## When to Use

* Large dataset
* CPU-intensive tasks
* Stateless operations

---

## When NOT to Use

* Web applications
* Database calls
* IO-heavy operations
* Small collections

Parallel is not always faster.

---
