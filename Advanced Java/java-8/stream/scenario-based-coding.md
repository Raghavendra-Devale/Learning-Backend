
---

# ✅ Scenario-Based Coding Questions 

These are the ones asked in 1–3 YOE backend interviews.

---

### Scenario 1: Remove Duplicate Users by Email

You have:

```java
class User {
    Long id;
    String email;
}
```

Requirement:
Remove duplicate users based on email.

Expected Solution:

```java
Collection<User> uniqueUsers =
    users.stream()
         .collect(Collectors.toMap(
             User::getEmail,
             Function.identity(),
             (existing, replacement) -> existing
         ))
         .values();
```

Tests:

* toMap duplicate trap
* Merge function knowledge

---

### Scenario 2: Get Top 3 Highest Paid Employees

```java
employees.stream()
         .sorted(Comparator.comparing(Employee::getSalary).reversed())
         .limit(3)
         .toList();
```

Tests:

* sorted (stateful)
* limit (short-circuit)
* Comparator usage

---

### Scenario 3: Group Orders by Status and Count Them

```java
orders.stream()
      .collect(Collectors.groupingBy(
          Order::getStatus,
          Collectors.counting()
      ));
```

Tests:

* groupingBy
* Downstream collector

---

### Scenario 4: Flatten Nested List

Orders → Items

```java
orders.stream()
      .flatMap(order -> order.getItems().stream())
      .toList();
```

Tests:

* flatMap understanding

---

### Scenario 5: Check If Any User is Admin

```java
boolean hasAdmin =
    users.stream()
         .anyMatch(user -> user.getRole() == Role.ADMIN);
```

Tests:

* Short-circuit
* anyMatch

---

### Scenario 6: Sum Revenue of Completed Orders Only

```java
double total =
    orders.stream()
          .filter(order -> order.getStatus() == Status.COMPLETED)
          .mapToDouble(Order::getAmount)
          .sum();
```

Tests:

* filter
* primitive stream
* mapToDouble

---

### Scenario 7: Convert List to Map (ID → User)

```java
Map<Long, User> userMap =
    users.stream()
         .collect(Collectors.toMap(
             User::getId,
             Function.identity()
         ));
```

Tests:

* toMap
* Identity function

---

# 🔥 Advanced Scenario (2–3 YOE Level)

### Scenario 8: Find Department with Highest Average Salary

```java
employees.stream()
         .collect(Collectors.groupingBy(
             Employee::getDepartment,
             Collectors.averagingDouble(Employee::getSalary)
         ))
         .entrySet()
         .stream()
         .max(Map.Entry.comparingByValue());
```

Tests:

* groupingBy
* averagingDouble
* stream chaining
* Optional handling

---