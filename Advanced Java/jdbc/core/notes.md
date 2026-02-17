# JDBC — Core Notes (0–3 YOE Backend)


## 1. Definition

JDBC (Java Database Connectivity) is a Java API used to interact with relational databases.

---

## 2. Architecture

Java Application → JDBC API → JDBC Driver → Database

---

## 3. JDBC Workflow

1. Obtain Connection
2. Create Statement
3. Execute SQL
4. Process ResultSet
5. Close resources

---

## 4. Connection

Represents database session.

DriverManager.getConnection(url, user, password)

Connection creation is expensive.

---

## 5. Statement Types

### Statement
- Vulnerable to SQL Injection
- Not preferred

### PreparedStatement
- Parameterized queries
- Prevents SQL injection
- Better performance
- Recommended

---

## 6. Execution Methods

executeQuery() → SELECT

executeUpdate() → INSERT/UPDATE/DELETE

---

## 7. ResultSet

Cursor-based result holder.

Important methods:
- next()
- getInt()
- getString()

---

## 8. Auto Commit

Default = true

Each statement commits automatically.

---

## 9. Transactions

setAutoCommit(false)
commit()
rollback()

Ensures atomic operations.

---

## 10. Resource Management

Use try-with-resources to prevent leaks.

---