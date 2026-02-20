
# HashMap Internals — Interview-Ready Deep Dive (0–3 Years Experience)

## 1. What HashMap Really Is (Mental Model)

A `HashMap` is basically:

> **An array + a hashing algorithm + collision management**

Think of it like a huge apartment building:

* The **array** = building floors (buckets)
* The **hash function** = receptionist deciding which floor a person goes to
* The **linked list/tree** = people waiting on that floor if multiple arrive

Goal:
👉 Find a value **without scanning everything**.

That’s why average lookup becomes **O(1)**.

---

## 2. Internal Structure (What Actually Exists Inside)

Internally (Java 8+):

```
Node<K,V>[] table   // main bucket array
```

Each bucket contains either:

* nothing (`null`)
* a **linked list of Nodes**
* a **Red-Black Tree** (after many collisions)

Each Node stores:

```
hash
key
value
next (pointer)
```

Important realization:

HashMap does NOT store data randomly.
It stores data based on **calculated bucket position**.

---

## 3. How `put(key, value)` Works — Step by Step

This is one of the most asked interview flows.

### Step 1 — hashCode()

```java
int hash = key.hashCode();
```

Every object can produce a hash value.

But raw hashCodes can be bad (clustered numbers).

---

### Step 2 — Hash Spreading (VERY IMPORTANT)

Java improves distribution:

```java
hash ^ (hash >>> 16)
```

Why?

Because arrays are small compared to possible hash values.
Mixing high bits into low bits reduces collisions.

Interview insight:

> HashMap does not blindly trust your hashCode().

---

### Step 3 — Bucket Index Calculation

```
index = (n - 1) & hash
```

Where `n` = array length.

Bitwise AND is much faster than modulo:

```
hash % n   ❌ slower
hash & (n-1) ✅ faster
```

This works ONLY because capacity is power of 2.

---

### Step 4 — Insert Logic

Case A: Bucket empty
→ create new node.

Case B: Bucket occupied

1. Compare hashes
2. Call `equals()` to check key equality

Important rule:

👉 `equals()` decides equality
👉 `hashCode()` decides location

If keys are equal → value replaced.
Else → node appended.

---

## 4. Why Capacity Is Always Power of 2 (Interview Favorite)

Example:

```
capacity = 16 → binary 10000
n - 1 = 15 → binary 01111
```

AND operation keeps only lower bits:

```
hash & 01111
```

Benefits:

* Extremely fast calculation
* Better bucket distribution
* Simple resize logic

Hidden insight interviewers love:

> During resize, entries either stay in same index or move by oldCapacity — no full recomputation needed.

That’s a brilliant optimization.

---

## 5. Collision Handling Evolution

### Java 7 (Old World)

Collisions → Linked List

Worst case:

```
All keys same bucket → O(n)
```

Attackers could exploit this using crafted hashes (Hash Collision DOS).

---

### Java 8+ (Modern Fix)

If:

```
bucket size > 8
AND table capacity ≥ 64
```

Linked list becomes:

👉 **Red-Black Tree**

Why 8?

Because experimentation showed tree overhead isn’t worth it for small lists.

Performance improves:

| Structure      | Lookup   |
| -------------- | -------- |
| Linked List    | O(n)     |
| Red-Black Tree | O(log n) |

---

## 6. Load Factor & Resizing (Where Performance Dies)

Default:

```
Initial capacity = 16
Load factor = 0.75
```

Resize threshold:

```
threshold = capacity × loadFactor
```

So:

```
16 × 0.75 = 12
```

When size reaches 13 → resize.

---

### What Happens During Resize?

1. New array created (double size)
2. All entries rehashed
3. Nodes redistributed

This is expensive:

👉 O(n) operation

Real backend lesson:

If you know large data size beforehand:

```java
new HashMap<>(expectedSize);
```

Prevents multiple resizes.

Senior engineers do this instinctively.

---

## 7. Performance Characteristics (Reality vs Theory)

| Operation | Average | Worst (Java 8+) |
| --------- | ------- | --------------- |
| put       | O(1)    | O(log n)        |
| get       | O(1)    | O(log n)        |
| remove    | O(1)    | O(log n)        |

Average case dominates because good hashing spreads keys evenly.

---

## 8. Thread Safety — Why HashMap Is Dangerous Concurrently

HashMap is NOT synchronized.

Problems in multithreading:

* Lost updates
* Visibility issues
* Structure corruption

### Famous Java 7 Bug

During resize, linked lists could form cycles → infinite loop → CPU 100%.

That bug terrified production systems.

---

### Correct Solution

Use:

```java
ConcurrentHashMap
```

It uses:

* bucket-level locking (Java 7)
* CAS + synchronized bins (Java 8+)

Result:

High concurrency without global lock.

---

## 9. Backend Reality (Why Interviewers Care)

HashMap sits everywhere:

* Spring dependency injection caches
* Hibernate entity tracking
* HTTP session storage
* JSON parsing
* Request attribute maps

A bad `hashCode()` implementation can silently destroy performance.

Example mistake:

```java
public int hashCode() {
    return 1; // everything same bucket
}
```

Congratulations — you invented a LinkedListMap.

---

## 10. MOST IMPORTANT INTERVIEW TRAPS

### Trap 1

“Why equals() AND hashCode() both?”

Correct answer:

> hashCode finds bucket, equals confirms equality inside bucket.

---

### Trap 2

“Can two unequal objects have same hashCode?”

Yes. Collision is allowed.

---

### Trap 3

“If hashCodes equal, are objects equal?”

No. equals() decides.

---

### Trap 4

“Why treeify only after capacity 64?”

Because resizing usually fixes collisions cheaply before tree overhead is needed.

---

## One Big Insight (Senior-Level Thinking)

HashMap is not fast because of magic.

It is fast because it trades:

* extra memory
* probabilistic distribution
* occasional expensive resize

for extremely fast average access.

Engineering is always trade-offs disguised as elegance.

---

