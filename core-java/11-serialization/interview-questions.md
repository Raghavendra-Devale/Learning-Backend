# Interview Questions – Serialization & Deserialization

---

## Q1. What is serialization?
**Answer:**
Serialization converts a Java object into a byte stream for storage or transmission.

---

## Q2. Is constructor called during deserialization?
**Answer:**
No. JVM reconstructs the object directly from the byte stream without invoking constructors.

---

## Q3. Why is serialVersionUID important?
**Answer:**
It ensures class compatibility during deserialization and prevents InvalidClassException.

---

## Q4. What fields are not serialized?
**Answer:**
static and transient fields.

---

## Q5. Why is Java serialization insecure?
**Answer:**
Because deserialization can execute malicious object graphs without constructor checks, leading to code execution.

---

## Q6. When should transient be used?
**Answer:**
For sensitive data, derived values, non-serializable fields, or temporary runtime data.

---

## Q7. Why is Java serialization discouraged in modern systems?
**Answer:**
Due to security risks, versioning issues, tight coupling, and poor performance.

---

## Common Interview Traps & Pitfalls

❌ Thinking constructors are called  
❌ Forgetting serialVersionUID  
❌ Assuming GC protects against deserialization attacks  
❌ Using serialization for APIs  

---

## One Interview-Safe Explanation

> “Java serialization is powerful but risky. It bypasses constructors during deserialization and can lead to security vulnerabilities, so modern backend systems prefer safer formats like JSON or Protobuf.”

---
