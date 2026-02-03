# Lesson 19: Serialization & Deserialization

This note explains Java serialization and deserialization, internal behavior, security risks, performance concerns, and best practices used in backend systems.

---

## 1. What Is Serialization?

Serialization is the process of converting a Java object into a byte stream so it can be:
- Stored
- Transmitted over a network
- Cached

Deserialization reconstructs the object from the byte stream.

---

## 2. How Java Serialization Works

To enable serialization:
```java
class User implements Serializable { }
````

Internally:

* JVM uses reflection
* Object state is restored directly from bytes
* **Constructors are NOT called**

This behavior is critical for understanding security risks.

---

## 3. serialVersionUID (Very Important)

`serialVersionUID` is a version identifier for a Serializable class.

```java
private static final long serialVersionUID = 1L;
```

Why it matters:

* Ensures compatibility during deserialization
* Prevents `InvalidClassException`
* Avoids JVM-generated unstable IDs

---

## 4. What Gets Serialized

Serialized:

* Instance fields
* Object references (recursively)

Not serialized:

* `static` fields
* `transient` fields

---

## 5. transient Keyword

`transient` fields are excluded from serialization.

Use `transient` for:

* Sensitive data (passwords, secrets)
* Derived values
* Non-serializable fields
* Temporary runtime data

---

## 6. Security Risks of Java Serialization

Java deserialization is dangerous because:

* Constructors are bypassed
* Malicious object graphs can be injected
* Dangerous methods can be executed during deserialization

This has caused real-world vulnerabilities.

---

## 7. Why Java Serialization Is Discouraged

Problems:

* Security vulnerabilities
* Tight class coupling
* Versioning issues
* Poor performance
* Hard debugging

Modern systems often avoid native Java serialization.

---

## 8. Safer Alternatives

Preferred formats:

* JSON (Jackson)
* XML
* Protobuf
* Avro

These are:

* Safer
* Explicit
* Language-independent

---

## 9. Backend Best Practices

* Avoid native Java serialization for external input
* Use `transient` carefully
* Define `serialVersionUID`
* Prefer JSON or Protobuf for APIs

---

## 10. Interview-Safe Summary

> “Java serialization converts objects into byte streams but is risky due to security and versioning issues. Constructors are bypassed during deserialization, so modern systems prefer safer formats like JSON.”

---

