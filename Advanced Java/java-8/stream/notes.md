# Java Streams — Complete Notes (0–3 YOE Backend Focus)

---

# 1. What is a Stream?

A Stream is a sequence of elements supporting functional-style operations.

Important:
- Not a data structure
- Does not store data
- Single-use
- Lazy
- Supports internal iteration

---

# 2. Why Streams?

Before Java 8:
- External iteration (for-loop)
- More boilerplate
- Harder parallelization
- More mutation-based code

Streams introduced:
- Declarative style
- Internal iteration
- Cleaner aggregation
- Easier parallelism

---

# 3. Stream Pipeline

Source → Intermediate Operations → Terminal Operation

Example:

users.stream()
.filter(User::isActive)
.map(User::getEmail)
.toList();

Without terminal operation → nothing executes.

---

# 4. Intermediate Operations

These are lazy.

- filter()
- map()
- flatMap()
- sorted()
- distinct()
- limit()
- skip()
- peek()

Stateful:
- sorted
- distinct
- limit (sometimes)

Stateless:
- filter
- map

---

# 5. Terminal Operations

These trigger execution.

- toList()
- forEach()
- collect()
- count()
- reduce()
- findFirst()
- findAny()
- anyMatch()
- allMatch()
- noneMatch()

---

# 6. Lazy Evaluation

Intermediate operations do not execute until terminal operation is called.

Enables:
- Optimization
- Short-circuiting
- Efficient processing

---

# 7. map vs flatMap

map():
1 element → 1 element

flatMap():
1 element → multiple elements → flattened

Example:

orders.stream()
.flatMap(order -> order.getItems().stream());

---

# 8. Short-Circuit Operations

- findFirst()
- findAny()
- anyMatch()
- limit()

These may stop processing early.

---

# 9. Single-Use Nature

Stream cannot be reused after terminal operation.

Throws IllegalStateException.

---

# 10. Collectors

collect() performs mutable reduction.

Must-know collectors:

- toList()
- toSet()
- toMap()
- groupingBy()
- partitioningBy()
- counting()
- summingDouble()
- averagingDouble()
- maxBy()
- minBy()

---

# 11. toMap() Duplicate Trap

Without merge function:
IllegalStateException if duplicate key exists.

Correct:

.toMap(
User::getId,
Function.identity(),
(u1, u2) -> u1
)

---

# 12. groupingBy vs partitioningBy

groupingBy:
Dynamic grouping.

partitioningBy:
Boolean split (true/false only).

---

# 13. Primitive Streams (Performance)

Use:
- IntStream
- LongStream
- DoubleStream

Example:

.mapToDouble(Employee::getSalary)
.sum();

Avoids boxing overhead.

---

# 14. Parallel Streams (Conceptual)

parallelStream():
Uses ForkJoinPool.commonPool()

Not always faster.

Avoid in:
- Web apps
- IO-heavy operations
- Small datasets

---

# 15. Common Mistakes

❌ No terminal operation  
❌ Reusing stream  
❌ Using forEach for accumulation  
❌ Ignoring duplicate keys in toMap  
❌ Blind parallelStream usage  
❌ Not handling Optional from maxBy

---

# 16. Backend Patterns

✔ Group by department  
✔ Count users by role  
✔ Sum revenue  
✔ Convert List to Map  
✔ Remove duplicates  
✔ Flatten nested lists  
✔ Sort API responses  
✔ Find first match

---

End of Streams Notes.
