# Connection Pooling Trap Questions

---

1. Does close() destroy connection?
   No, it returns connection to pool.

---

2. Increasing pool size always improves performance?
   No. DB has limits.

---

3. One connection per request good design?
   No.

---

4. Connection leak caused by DB?
   No, caused by application not closing connections.

---

5. Is connection pool part of JDBC?
   No. It is an additional layer.

---