# Date & Time API — Twisted Questions

---

### 1️⃣ Is `LocalDate` mutable?

**Answer:**
No.

**Explanation:**

`LocalDate` is immutable.
Once created, its state cannot be changed.

Any modification method like `plusDays()` returns a new instance.

---

### 2️⃣ Does `plusDays()` modify the original object?

**Answer:**
No.

**Explanation:**

All `java.time` classes are immutable.

Example:

```java
LocalDate date = LocalDate.now();
LocalDate newDate = date.plusDays(5);
```

Here, `date` remains unchanged.
`newDate` is a separate object.

---

### 3️⃣ Can `LocalDate` handle timezone?

**Answer:**
No.

**Explanation:**

`LocalDate` represents only a date (year, month, day).
It has no time and no timezone information.

For timezone-aware values, use:

* `ZonedDateTime`
* `OffsetDateTime`
* `Instant`

---

### 4️⃣ Why is `Date` problematic in multithreading?

**Answer:**
Because it is mutable.

**Explanation:**

`java.util.Date` objects can be modified after creation.

If shared across threads, one thread can change the value while another is using it, leading to inconsistent behavior.

`java.time` classes are immutable and therefore thread-safe.

---

### 5️⃣ Which should you store in DB — `LocalDateTime` or `Instant`?

**Answer:**
Usually `Instant`.

**Explanation:**

* `Instant` represents a moment in UTC.
* It avoids timezone ambiguity.
* It is ideal for distributed systems.

Best practice:

* Store timestamps in UTC (`Instant`).
* Convert to user timezone at presentation layer.

Using `LocalDateTime` can cause ambiguity in global systems because it has no timezone context.

---