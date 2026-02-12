# Java 8 Date & Time API  Complete Notes

---

# 1. Why Was It Introduced?

Before Java 8, developers used:

* `java.util.Date`
* `java.util.Calendar`
* `SimpleDateFormat`

Problems with old API:

* Mutable (can be modified)
* Not thread-safe
* Confusing design
* Poor timezone handling
* Difficult date manipulation

To solve these issues, Java 8 introduced the `java.time` package (JSR-310), inspired by Joda-Time.

---

# 2. Core Classes (Most Important)

---

## LocalDate

Represents date only (no time, no timezone).

Example:

* 2026-02-12

Use when:

* Storing birth date
* Storing invoice date
* Storing only calendar date

---

## LocalTime

Represents time only (no date, no timezone).

Example:

* 14:30:00

Use when:

* Store business opening time
* Store time-of-day value

---

## LocalDateTime

Represents date + time (no timezone).

Example:

* 2026-02-12T14:30

Use when:

* Logging local events
* Internal system timestamps (no timezone context)

---

## ZonedDateTime

Represents date + time + timezone.

Example:

* 2026-02-12T14:30+05:30[Asia/Kolkata]

Use when:

* Working with global systems
* Converting between timezones
* User-facing timestamps

---

## Instant (Important for Backend)

Represents a point in time in UTC.

Example:

* 2026-02-12T09:00:00Z

Best for:

* Storing timestamps in database
* Distributed systems
* Event logs

---

# 3. Creating Date & Time Objects

---

## LocalDate

```java
LocalDate date = LocalDate.of(2026, 2, 12);
LocalDate today = LocalDate.now();
```

---

## LocalTime

```java
LocalTime time = LocalTime.of(14, 30);
LocalTime now = LocalTime.now();
```

---

## LocalDateTime

```java
LocalDateTime dateTime =
    LocalDateTime.of(2026, 2, 12, 14, 30);
```

---

## ZonedDateTime

```java
ZonedDateTime zdt =
    ZonedDateTime.now(ZoneId.of("Asia/Kolkata"));
```

---

# 4. Immutability (Very Important)

All classes in `java.time` are immutable.

Example:

```java
LocalDate date = LocalDate.now();
LocalDate nextWeek = date.plusDays(7);
```

`date` remains unchanged.

This makes the API:

* Thread-safe
* Safer
* Predictable

---

# 5. Date & Time Manipulation

---

## Add / Subtract

```java
date.plusDays(5);
date.minusMonths(2);
date.plusYears(1);
```

---

## Time Manipulation

```java
time.plusHours(2);
time.minusMinutes(30);
```

---

## Using withX Methods

```java
date.withDayOfMonth(1);
dateTime.withHour(10);
```

These return new objects.

---

# 6. Comparison

Used for validation and business rules.

---

## Methods

```java
date1.isBefore(date2);
date1.isAfter(date2);
date1.isEqual(date2);
```

---

## compareTo

```java
date1.compareTo(date2);
```

Returns:

* Negative → before
* Zero → equal
* Positive → after

---

# 7. Formatting & Parsing

Handled by `DateTimeFormatter`.

---

## Formatting

```java
DateTimeFormatter formatter =
    DateTimeFormatter.ofPattern("dd-MM-yyyy");

String formatted = date.format(formatter);
```

---

## Parsing

```java
LocalDate parsed =
    LocalDate.parse("12-02-2026", formatter);
```

---

## Common Patterns

* yyyy-MM-dd
* dd/MM/yyyy
* HH:mm:ss
* yyyy-MM-dd HH:mm:ss

---

# 8. Period vs Duration

---

## Period

Used for date-based differences.

Example:

```java
Period period =
    Period.between(startDate, endDate);
```

Returns difference in:

* Years
* Months
* Days

Use when:

* Age calculation
* Subscription validity

---

## Duration

Used for time-based differences.

Example:

```java
Duration duration =
    Duration.between(startTime, endTime);
```

Returns difference in:

* Hours
* Minutes
* Seconds
* Milliseconds

Use when:

* Session timeout
* Execution time
* Token expiry

---

# 9. Timezone Handling (Backend Critical)

---

## ZoneId

```java
ZoneId.of("Asia/Kolkata");
ZoneId.systemDefault();
```

---

## Convert Timezone

```java
ZonedDateTime indiaTime =
    ZonedDateTime.now(ZoneId.of("Asia/Kolkata"));

ZonedDateTime usTime =
    indiaTime.withZoneSameInstant(ZoneId.of("America/New_York"));
```

Important for global applications.

---

# 10. Converting Between Old and New API

---

## Date to Instant

```java
Date date = new Date();
Instant instant = date.toInstant();
```

---

## Instant to Date

```java
Date date = Date.from(instant);
```

Needed when working with legacy systems.

---

# 11. Backend Best Practices

---

✔ Use `Instant` for database timestamps
✔ Store UTC time in database
✔ Convert to user timezone at presentation layer
✔ Avoid `LocalDateTime` for global systems
✔ Prefer immutable types
✔ Avoid old Date/Calendar API

---

# 12. Common Mistakes

---

❌ Using `LocalDateTime` for global timestamps
❌ Ignoring timezone differences
❌ Storing local time without context
❌ Using `new Date()` in new code
❌ Forgetting immutability (expecting object to change)

---

# 13. Typical Backend Scenarios

---

### 1️⃣ Token Expiry Check

```java
Instant now = Instant.now();
if (now.isAfter(tokenExpiryInstant)) {
    // token expired
}
```

---

### 2️⃣ Calculate User Age

```java
Period age =
    Period.between(birthDate, LocalDate.now());
```

---

### 3️⃣ Format Date for API Response

```java
DateTimeFormatter formatter =
    DateTimeFormatter.ofPattern("yyyy-MM-dd");

String response = date.format(formatter);
```

---

# Key Interview Summary

* New API is immutable and thread-safe.
* `LocalDateTime` has no timezone.
* `Instant` represents UTC timestamp.
* `Period` is date-based; `Duration` is time-based.
* Always handle timezone carefully in backend systems.

---