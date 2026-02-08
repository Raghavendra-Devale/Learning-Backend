# 📚 Java Collections Framework — Index

This section contains **complete, interview-focused notes** on the **Java Collections Framework**,
with emphasis on **how to choose the right collection**, **internal working**, and
**real backend trade-offs**.

Each topic is organized into:
- 📘 **notes.md** → concepts + internals
- 🎯 **interview-questions.md** → fast revision, traps & edge cases

Additionally, a **Twisted Questions track** exists to handle indirect and confusing interview questions.

---

## ✅ Collections — Status

**Level Covered:** Strong Fresher → Junior Backend (0–2 YOE)

This section is sufficient for:
- Java fresher interviews
- Junior backend roles
- Confident, decision-based answers in collections
- Handling indirect / twisted collections questions

---

## 🗂 Collections Index

### 01. HashMap Internals
📁 Folder: `01-hashmap-internals`

**Focus**
- Hashing & bucket structure
- Collisions & chaining
- Load factor & resizing
- Java 8 treeification (Red-Black Tree)
- `equals()` / `hashCode()` contract
- Common interview pitfalls

- 📘 [Notes](./01-hashmap-internals/notes.md)
- 🎯 [Interview Questions](./01-hashmap-internals/interview-questions.md)

---

### 02. ConcurrentHashMap
📁 Folder: `02-concurrenthashmap`

**Focus**
- Thread-safety guarantees
- Java 7 vs Java 8 internal design
- CAS & lock granularity
- Performance vs `synchronizedMap`
- Backend concurrency scenarios

- 📘 [Notes](./02-concurrenthashmap/notes.md)
- 🎯 [Interview Questions](./02-concurrenthashmap/interview-questions.md)

---

### 03. ArrayList vs LinkedList
📁 Folder: `03-arraylist-vs-linkedlist`

**Focus**
- Internal data structures
- Memory overhead & cache locality
- Time complexity (read / write / insert)
- Real backend usage
- Interview misconceptions

- 📘 [Notes](./03-arraylist-vs-linkedlist/notes.md)
- 🎯 [Interview Questions](./03-arraylist-vs-linkedlist/interview-questions.md)

---

### 04. Set Implementations
📁 Folder: `04-set-implementations`

**Focus**
- HashSet internals
- LinkedHashSet ordering
- TreeSet uniqueness logic
- Comparator pitfalls
- Ordering vs sorting

- 📘 [Notes](./04-set-implementations/notes.md)
- 🎯 [Interview Questions](./04-set-implementations/interview-questions.md)

---

### 05. Queue & Deque
📁 Folder: `05-queue-deque`

**Focus**
- Queue vs Deque
- ArrayDeque vs LinkedList
- Stack using Deque (modern approach)
- Performance considerations
- Backend usage patterns

- 📘 [Notes](./05-queue-deque/notes.md)
- 🎯 [Interview Questions](./05-queue-deque/interview-questions.md)

---

### 06. Iterator & Fail-Fast vs Fail-Safe
📁 Folder: `06-iterator-failfast`

**Focus**
- Iterable vs Iterator
- for-each loop internals
- Structural modification
- ConcurrentModificationException
- Fail-fast vs fail-safe behavior

- 📘 [Notes](./06-iterator-failfast/notes.md)
- 🎯 [Interview Questions](./06-iterator-failfast/interview-questions.md)

---

### 07. Comparable vs Comparator (Advanced)
📁 Folder: `07-comparable-comparator-advanced`

**Focus**
- Natural vs external ordering
- Consistency with `equals()`
- TreeSet / TreeMap pitfalls
- Comparator chaining
- Overflow & null handling

- 📘 [Notes](./07-comparable-comparator-advanced/notes.md)
- 🎯 [Interview Questions](./07-comparable-comparator-advanced/interview-questions.md)

---

### 08. Map Implementations & Design Choices
📁 Folder: `08-map-implementations`

**Focus**
- HashMap vs LinkedHashMap vs TreeMap
- Ordering vs sorting
- LRU cache using LinkedHashMap
- Performance trade-offs
- Backend selection criteria

- 📘 [Notes](./08-map-implementations/notes.md)
- 🎯 [Interview Questions](./08-map-implementations/interview-questions.md)

---

## 🧠 Twisted / Indirect Questions (Collections)

📁 Located at root of `collections/`

This file contains **indirect, scenario-based, and confusing questions**
commonly asked to test real understanding instead of API knowledge.

**Covers**
- “Which collection would you choose?” traps
- Performance vs memory twists
- Concurrency misconceptions
- Null-handling edge cases
- Iterator & modification traps
- Backend design scenarios

- 🧠 [Twisted Collections Questions](./twisted-questions.md)

---

## 🎯 How to Revise Collections (Interview Mode)

1. Start with **interview-questions.md**
2. Refer **notes.md** only for clarity
3. Before interviews:
   - Read **twisted-questions.md**
   - Practice explaining *why* a collection was chosen
4. Think in terms of:
   - Uniqueness
   - Ordering
   - Access pattern
   - Concurrency
   - Memory

---

## 🧠 Author’s Note

This Collections section focuses on:
- Decision-making over memorization
- Internals over surface-level APIs
- Handling indirect and twisted questions confidently

This index is the **single entry point** for Java Collections revision.

---
