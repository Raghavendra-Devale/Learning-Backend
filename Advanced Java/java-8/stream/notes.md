---

# ✅ PART 1 — Java Streams (Core Fundamentals)

---

# 1️⃣ What is a Stream?

### Interview-Ready Definition

A Stream in Java is a sequence of elements that supports functional-style operations to process data declaratively.

Then simplify it:

It allows us to perform operations like filtering, mapping, sorting, and aggregation on collections using a pipeline model.

---

## Key Characteristics (Must Mention)

* Not a data structure
* Does not store data
* Works on a data source (Collection, array, etc.)
* Supports internal iteration
* Lazy
* Single-use

---

## Internal vs External Iteration

### External Iteration (Before Java 8)

```java
for (User user : users) {
    if (user.isActive()) {
        System.out.println(user.getEmail());
    }
}
```

You control iteration.

---

### Internal Iteration (Streams)

```java
users.stream()
     .filter(User::isActive)
     .map(User::getEmail)
     .forEach(System.out::println);
```

Stream API controls iteration internally.

Interview keyword: **internal iteration**

---

# 2️⃣ Stream Pipeline (Very Important)

A Stream pipeline consists of:

```
Source → Intermediate Operations → Terminal Operation
```

Example:

```java
users.stream()               // Source
     .filter(User::isActive) // Intermediate
     .map(User::getEmail)    // Intermediate
     .toList();              // Terminal
```

---

## Important Rule

Without a terminal operation, nothing executes.

Streams are lazy.

---

# 3️⃣ Intermediate Operations

Intermediate operations:

* Return a Stream
* Are lazy
* Build the pipeline

Common ones:

* filter()
* map()
* flatMap()
* sorted()
* distinct()
* limit()
* skip()
* peek()

---

## Stateless vs Stateful

### Stateless

Do not depend on other elements.

* filter
* map

### Stateful

Require processing entire stream.

* sorted
* distinct
* limit (sometimes)

Interview tip: Mention stateful operations may require buffering.

---

# 4️⃣ Terminal Operations

Terminal operations:

* Trigger execution
* Produce result

Examples:

* toList()
* collect()
* count()
* reduce()
* findFirst()
* findAny()
* anyMatch()
* allMatch()
* noneMatch()

---

# 5️⃣ Lazy Evaluation

Intermediate operations do not execute until terminal operation is called.

Example:

```java
users.stream()
     .filter(user -> {
         System.out.println("Filtering");
         return user.isActive();
     });
```

Nothing prints.

After:

```java
.toList();
```

Now it executes.

---

## Why Lazy Evaluation Matters

* Enables short-circuiting
* Improves performance
* Processes element by element

---

# 6️⃣ map vs flatMap (Most Important Concept)

### map()

1 element → 1 element

```java
.map(User::getEmail)
```

---

### flatMap()

1 element → multiple elements → flattened

Example:

Order → List<Item>

```java
orders.stream()
      .flatMap(order -> order.getItems().stream())
      .toList();
```

---

## Interview Explanation

map transforms elements.

flatMap flattens nested structures.

If your mapping function returns a Stream → use flatMap.

---

# 7️⃣ Short-Circuit Operations

These may stop processing early:

* findFirst
* findAny
* anyMatch
* limit

Example:

```java
users.stream()
     .filter(User::isActive)
     .findFirst();
```

Stops once first match is found.

---

# 8️⃣ Single-Use Nature

Streams cannot be reused.

```java
Stream<User> stream = users.stream();
stream.count();
stream.toList(); // IllegalStateException
```

Reason: Streams are consumed after terminal operation.

---

# 9️⃣ reduce() (Often Asked)

Used to combine elements.

Example:

```java
int sum = numbers.stream()
                 .reduce(0, Integer::sum);
```

reduce performs immutable reduction.

Interview difference:

* reduce → immutable reduction
* collect → mutable reduction

---

# 10️⃣ Optional in Streams

Some terminal operations return Optional:

* findFirst
* max
* min

Never do:

```java
.max(...).get();
```

Better:

```java
.orElseThrow();
```

---