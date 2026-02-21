# JDBC — Generated Keys (Auto Increment IDs)

---

## 1. Problem Statement

Many database tables generate primary keys automatically.

Example:

CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50)
);

When inserting:

INSERT INTO users(name) VALUES ('Raghu');

Database generates the ID automatically.

The application often needs this generated ID immediately.

---

## 2. Why Generated Keys Are Needed

Common backend scenarios:

- Creating related records after insert
- Returning created resource ID in API response
- Logging or auditing
- Parent-child entity creation

Example:
Create User → create Address using user_id.

---

## 3. How JDBC Retrieves Generated Keys

JDBC allows retrieval of auto-generated keys after INSERT.

Steps:

1. Prepare statement with RETURN_GENERATED_KEYS
2. Execute INSERT
3. Fetch generated keys using getGeneratedKeys()

---

## 4. Example

PreparedStatement ps =
    connection.prepareStatement(
        "INSERT INTO users(name) VALUES (?)",
        Statement.RETURN_GENERATED_KEYS
    );

ps.setString(1, "Raghu");

ps.executeUpdate();

ResultSet keys = ps.getGeneratedKeys();

if (keys.next()) {
    int id = keys.getInt(1);
}

---

## 5. Important Points

- Generated keys are returned as ResultSet.
- executeUpdate() returns affected row count, NOT ID.
- Must explicitly request keys using RETURN_GENERATED_KEYS.
- Works mainly with auto-increment or identity columns.

---

## 6. Backend Usage Pattern

Typical API flow:

Insert record → fetch generated ID → return response.

Example response:

{
  "id": 101,
  "name": "Raghu"
}

---

## 7. Common Mistakes

❌ Forgetting RETURN_GENERATED_KEYS  
❌ Expecting executeUpdate() to return ID  
❌ Not calling keys.next() before reading value  

---
