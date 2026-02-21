# JDBC — Final Concepts (0–3 YOE)

---

## executeQuery vs executeUpdate vs execute

executeQuery()
- Used for SELECT
- Returns ResultSet

executeUpdate()
- Used for INSERT/UPDATE/DELETE
- Returns affected row count

execute()
- Generic execution method
- Returns boolean

---

## Batch Processing

Used for bulk operations.

Methods:
addBatch()
executeBatch()

Improves performance by reducing DB round trips.

---

## CallableStatement

Used to call stored procedures.

prepareCall("{call procedure(?)}")

---

## SQLException Handling

Provides:
- Error message
- SQL state
- Vendor error code

Should be handled specifically.

---

## Resource Management

Close order:
ResultSet → Statement → Connection

Prefer try-with-resources.

---

## Limitations of JDBC

- Boilerplate code
- Manual mapping
- Hard transaction management

Led to ORM frameworks like Hibernate/JPA.

---
