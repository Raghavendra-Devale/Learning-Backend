# Date & Time API  Interview Questions
---

# 🔹 0 Level

---

### 1️⃣ Why was `java.time` introduced?

`java.time` was introduced in Java 8 to replace the old `Date` and `Calendar` APIs.

Old API problems:

* Mutable
* Not thread-safe
* Confusing design
* Poor timezone handling

The new API is:

* Immutable
* Thread-safe
* Cleaner and more intuitive
* Better at handling timezones

---

### 2️⃣ Difference between Date and LocalDate?

`Date` (old API):

* Mutable
* Represents both date and time
* Includes timezone internally
* Not thread-safe

`LocalDate` (java.time):

* Immutable
* Represents only date (no time, no timezone)
* Thread-safe
* Clearer API

---

# 🔹 Fresher Level

---

### 1️⃣ What is LocalDateTime?

`LocalDateTime` represents date and time without timezone information.

Example:

* 2026-02-12T14:30

It is used when timezone context is not required.

---

### 2️⃣ Are java.time classes mutable?

No.

All `java.time` classes are immutable.

Operations like `plusDays()` return a new object instead of modifying the existing one.

---

### 3️⃣ How do you format a date?

Using `DateTimeFormatter`.

Example:

```java
DateTimeFormatter formatter =
    DateTimeFormatter.ofPattern("dd-MM-yyyy");

String formatted = date.format(formatter);
```

---

### 4️⃣ How do you parse a string to date?

Using `LocalDate.parse()` with a formatter.

Example:

```java
LocalDate date =
    LocalDate.parse("12-02-2026", formatter);
```

---

### 5️⃣ Difference between Period and Duration?

Period:

* Date-based
* Measures years, months, days

Duration:

* Time-based
* Measures hours, minutes, seconds

Use Period for age calculation.
Use Duration for time intervals.

---

# 🔹 1–2 YOE

---

### 1️⃣ When would you use ZonedDateTime?

Use `ZonedDateTime` when:

* Working with multiple timezones
* Displaying user-specific time
* Converting between timezones

It contains date, time, and timezone information.

---

### 2️⃣ How to compare two dates?

Using:

```java
date1.isBefore(date2);
date1.isAfter(date2);
date1.isEqual(date2);
```

Or:

```java
date1.compareTo(date2);
```

---

### 3️⃣ How to calculate expiry date?

Example:

```java
LocalDate expiry = LocalDate.now().plusDays(30);
```

For token expiry:

```java
Instant expiry = Instant.now().plus(Duration.ofMinutes(15));
```

---

### 4️⃣ Why is java.time thread-safe?

Because all classes are immutable.

Once created, objects cannot be modified, making them safe in multi-threaded environments.

---

### 5️⃣ How would you store timestamps in DB?

Best practice:

* Store timestamps in UTC
* Use `Instant`
* Convert to user timezone at presentation layer

Avoid storing local timezone-based timestamps in distributed systems.

---

# 🔹 2–3 YOE

---

### 1️⃣ How does timezone affect backend systems?

Timezone affects:

* User-visible timestamps
* Scheduling systems
* Expiry calculations
* Distributed systems

Incorrect timezone handling can cause:

* Data inconsistency
* Wrong expiry logic
* Reporting errors

Backend systems should standardize on UTC internally.

---

### 2️⃣ How to handle user timezone in API?

Approach:

1. Store timestamps in UTC (`Instant`).
2. Convert to user’s timezone when returning API response.

Example:

```java
instant.atZone(userZoneId);
```

Timezone conversion should be done at presentation layer.

---

### 3️⃣ When would you use Instant?

Use `Instant` when:

* Storing database timestamps
* Logging events
* Distributed systems
* Token expiry logic

It represents a precise moment in UTC.

---

### 4️⃣ What problems existed with old Date API?

* Mutable objects
* Not thread-safe
* Complex timezone handling
* Confusing API design
* Poor formatting API

It often led to bugs and concurrency issues.

---

### 5️⃣ Difference between Instant and LocalDateTime?

Instant:

* Represents a moment in UTC
* Suitable for storage and system-level timestamps
* Timezone-aware (UTC)

LocalDateTime:

* Represents date and time without timezone
* Suitable for local calculations
* Not ideal for global systems

Use Instant for backend persistence.
Use LocalDateTime when timezone is irrelevant.

---