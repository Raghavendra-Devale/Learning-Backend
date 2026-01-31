
# Lesson 11: ArrayList vs LinkedList

This note explains the internal working and performance characteristics of `ArrayList` and `LinkedList` from an interview and backend perspective.

---

## 1. Common Ground

Both `ArrayList` and `LinkedList`:
- Implement the `List` interface
- Allow duplicates
- Maintain insertion order

The difference lies in **internal data structure**.

---

## 2. ArrayList Internals

`ArrayList` is backed by a **resizable array**.

### Key Characteristics
- Contiguous memory
- Fast random access
- Low memory overhead

---

### Performance

| Operation | Complexity |
|---------|------------|
| get(index) | O(1) |
| add(element) | O(1) amortized |
| add(index, element) | O(n) |
| remove(index) | O(n) |

---

### Resizing
- Initial capacity: 10
- Grows dynamically (approximately 1.5x)
- Resize requires copying elements

---

## 3. LinkedList Internals

`LinkedList` is a **doubly linked list**.

Each node stores:
- Data
- Reference to previous node
- Reference to next node

---

### Performance

| Operation | Complexity |
|---------|------------|
| addFirst / addLast | O(1) |
| removeFirst / removeLast | O(1) |
| get(index) | O(n) |

---

## 4. Important Performance Truth

❌ “LinkedList is faster for insertion and deletion”  

✅ Correct understanding:
- LinkedList insertion/deletion is O(1) **only if node reference is known**
- Insertion/deletion by index requires traversal → O(n)

---

## 5. Memory & Cache Behavior

### ArrayList
- Stores only data
- Excellent cache locality
- Efficient iteration

### LinkedList
- Stores data + two references per node
- High memory overhead
- Poor cache locality due to pointer chasing

---

## 6. Backend Usage Guidelines

### Prefer ArrayList When:
- Frequent reads
- Iteration-heavy logic
- Index-based access
- General-purpose lists

### Prefer LinkedList When:
- Frequent insert/remove at head or tail
- Queue or deque behavior
- Minimal random access

In real backend systems, `ArrayList` is used far more often.


