# JDBC Generated Keys — Twisted / Trap Questions

---

1. Does executeUpdate() return generated ID?
   No. It returns affected row count.

---

2. Will getGeneratedKeys() work without RETURN_GENERATED_KEYS?
   No.

---

3. Why does this fail?

   ResultSet keys = ps.getGeneratedKeys();
   int id = keys.getInt(1);

   Answer:
   keys.next() was not called.

---

4. Are generated keys returned as an integer directly?
   No. They are returned as ResultSet.

---

5. Can generated keys be retrieved for SELECT queries?
   No. Only for INSERT operations generating values.

---
