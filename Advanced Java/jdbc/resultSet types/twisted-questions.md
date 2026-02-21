# JDBC ResultSet Trap Questions

---

1. Does ResultSet start at first row?
   No. It starts before first row.

---

2. Can you call getString() before next()?
   No.

---

3. Can default ResultSet move backward?
   No.

---

4. Is scrollable ResultSet faster?
   No. Usually slower due to buffering.

---

5. Is CONCUR_UPDATABLE commonly used in modern backend apps?
   No.

---

