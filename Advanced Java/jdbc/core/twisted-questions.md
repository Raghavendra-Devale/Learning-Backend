# JDBC Twisted / Trap Questions

---

1. Is JDBC a driver?
   Answer: No, it is an API.

---

2. Which is safer: Statement or PreparedStatement?
   Answer: PreparedStatement.

---

3. Does executeQuery work for INSERT?
   Answer: No.

---

4. What happens if autoCommit is true?
   Answer: Each statement commits automatically.

---

5. Why is this dangerous?

   con.setAutoCommit(false);
   // no commit or rollback

   Answer:
   Transaction may remain open causing locks.

---

6. Does closing Connection close Statement and ResultSet?
   Answer:
   Yes (but still best practice to close explicitly).

---
