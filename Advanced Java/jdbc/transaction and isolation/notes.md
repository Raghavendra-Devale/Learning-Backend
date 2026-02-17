# JDBC Transactions & Isolation Levels

---

## Transaction

A transaction is a group of database operations executed as a single unit.

---

## ACID Properties

Atomicity
Consistency
Isolation
Durability

---

## Auto Commit

Default = true

Each SQL statement commits automatically.

Disable:

connection.setAutoCommit(false);

---

## Transaction Control

commit() → save changes
rollback() → undo changes

---

## Isolation Problems

Dirty Read
Non-repeatable Read
Phantom Read

---

## Isolation Levels

READ_UNCOMMITTED
READ_COMMITTED
REPEATABLE_READ
SERIALIZABLE

---

## Setting Isolation

connection.setTransactionIsolation(level);

---
