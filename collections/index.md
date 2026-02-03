# 📚 Java Collections Framework — Index

This section contains **completed, in-depth notes** on the **Java Collections Framework** with a strong focus on:
- Internal working
- Performance characteristics
- Concurrency behavior
- Interview traps & real backend usage

Each topic is organized into:
- 📘 **notes.md** → concept + internals
- 🎯 **interview-questions.md** → fast revision & traps

---

## ✅ Collections — Status: COMPLETED

This section is sufficient for:
- Java fresher interviews
- Junior backend roles
- Real-world backend decision making

---

## 🗂 Topics Covered

### 01. HashMap Internals
📁 Folder: `01-hashmap-internals`

- 📘 [Notes](./01-hashmap-internals/notes.md)
- 🎯 [Interview Questions](./01-hashmap-internals/interview-questions.md)

**Covers:**
- HashMap structure & hashing
- Buckets, collisions, chaining
- Load factor & resizing
- Java 8 treeification (Red-Black Tree)
- `equals()` / `hashCode()` impact
- Common interview pitfalls

---

### 02. ConcurrentHashMap
📁 Folder: `02-concurrenthashmap`

- 📘 [Notes](./02-concurrenthashmap/notes.md)
- 🎯 [Interview Questions](./02-concurrenthashmap/interview-questions.md)

**Covers:**
- Thread safety guarantees
- Java 7 vs Java 8 internal design
- CAS & lock granularity
- Performance vs `synchronizedMap`
- Backend concurrency scenarios

---

### 03. ArrayList vs LinkedList
📁 Folder: `03-arraylist-vs-linkedlist`

- 📘 [Notes](./03-arraylist-vs-linkedlist/notes.md)
- 🎯 [Interview Questions](./03-arraylist-vs-linkedlist/interview-questions.md)

**Covers:**
- Internal data structures
- Memory overhead & cache locality
- Time complexity (read/write/insert)
- Real backend use cases
- Interview misconceptions

---

### 04. Set Implementations
📁 Folder: `04-set-implementations`

- 📘 [Notes](./04-set-implementations/notes.md)
- 🎯 [Interview Questions](./04-set-implementations/interview-questions.md)

**Covers:**
- HashSet internals
- TreeSet uniqueness logic
- Comparator pitfalls
- Ordering vs sorting
- Interview traps

---

### 05. Queue & Deque
📁 Folder: `05-queue-deque`

- 📘 [Notes](./05-queue-deque/notes.md)
- 🎯 [Interview Questions](./05-queue-deque/interview-questions.md)

**Covers:**
- Queue vs Deque
- ArrayDeque vs LinkedList
- Stack using Deque
- Performance considerations
- Backend usage patterns

---

### 06. Iterator & Fail-Fast vs Fail-Safe
📁 Folder: `06-iterator-failfast`

- 📘 [Notes](./06-iterator-failfast/notes.md)
- 🎯 [Interview Questions](./06-iterator-failfast/interview-questions.md)

**Covers:**
- Iterable vs Iterator
- for-each loop internals
- Structural modification
- ConcurrentModificationException
- Fail-fast vs fail-safe behavior

---

### 07. Comparable vs Comparator (Advanced)
📁 Folder: `07-comparable-comparator-advanced`

- 📘 [Notes](./07-comparable-comparator-advanced/notes.md)
- 🎯 [Interview Questions](./07-comparable-comparator-advanced/interview-questions.md)

**Covers:**
- Natural vs external ordering
- Consistency with `equals()`
- TreeSet / TreeMap pitfalls
- Comparator chaining
- Overflow & null handling

---

### 08. Map Implementations
📁 Folder: `08-map-implementations`

- 📘 [Notes](./08-map-implementations/notes.md)
- 🎯 [Interview Questions](./08-map-implementations/interview-questions.md)

**Covers:**
- HashMap vs LinkedHashMap vs TreeMap
- Ordering vs sorting
- LRU cache using LinkedHashMap
- Performance trade-offs
- Backend selection criteria

---

## 🧠 How to Revise Collections (Interview Mode)

1. Read **interview-questions.md** of each topic
2. Jump to **notes.md** only if clarity is needed
3. Focus on:
   - Why this collection?
   - Internal working
   - Trade-offs

---

## 📝 Notes

- Collections knowledge here is **interview-ready**
- Focus is on **decision-making**, not API memorization
- Covers common traps that eliminate candidates

> This index is the **single entry point** for Java Collections revision.
