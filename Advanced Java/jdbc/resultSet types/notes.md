# JDBC ResultSet Types & Cursor Behavior

---

## ResultSet Cursor

ResultSet represents query results using a cursor.

Cursor starts BEFORE first row.

Must call rs.next() to move to first row.

---

## Default Type

TYPE_FORWARD_ONLY

- Move only forward
- Fastest
- Memory efficient
- Most commonly used

---

## Scrollable ResultSet

Requested explicitly.

TYPE_SCROLL_INSENSITIVE
- Can move forward/backward
- Snapshot view

TYPE_SCROLL_SENSITIVE
- Reflects DB changes (rare)

---

## Concurrency Types

CONCUR_READ_ONLY (default)
- Read-only access

CONCUR_UPDATABLE
- Allows updating rows via ResultSet

---

## Navigation Methods

next()
previous()
first()
last()
absolute(int row)

---

## Best Practice

Use forward-only read-only ResultSet for backend applications.

---
