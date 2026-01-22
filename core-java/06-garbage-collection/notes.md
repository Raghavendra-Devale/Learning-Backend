
# Lesson 6: Garbage Collection (GC)

This note explains how **Garbage Collection works in Java**, focusing on correct mental models required for backend interviews and real-world applications.

---

## 1. What Is Garbage Collection?

Garbage Collection is a JVM process that **automatically reclaims heap memory** by removing objects that are no longer reachable.

GC is:
- Automatic
- JVM-controlled
- Based on reachability

GC is NOT:
- Manual
- Immediate
- Guaranteed to run on demand

---

## 2. Reachability & GC Roots

An object becomes eligible for garbage collection if it is **not reachable from any GC root**.

### Common GC Roots
- Active thread stacks (local variables)
- Static variables
- JNI references

If an object is reachable from any of these, it will not be collected.

---

## 3. Generational Garbage Collection

The JVM divides heap memory into generations based on object lifetime.

### Why Generations Exist
Most objects die young.  
Generational GC improves performance by collecting short-lived objects frequently.

---

## 4. Heap Structure (High Level)

```

Heap
├── Young Generation
│   ├── Eden
│   ├── Survivor S0
│   └── Survivor S1
└── Old Generation

```

---

## 5. Young Generation

- New objects are allocated in Eden
- Minor GC occurs frequently
- Surviving objects move between Survivor spaces
- Long-living objects are promoted to Old Generation

---

## 6. Types of Garbage Collection

### Minor GC
- Runs on Young Generation
- Fast and frequent
- Causes short pauses

### Major / Full GC
- Runs on Old Generation (and sometimes entire heap)
- Slower and expensive
- Causes longer pauses

---

## 7. Stop-The-World (STW)

During GC, **all application threads are paused**.
This pause is called Stop-The-World.

STW can cause:
- Latency spikes
- Slow API responses
- Throughput drops

Modern GCs aim to minimize STW impact.

---

## 8. System.gc()

Calling `System.gc()`:
- Does NOT force GC
- Only sends a request to JVM
- JVM may ignore the request

---

## 9. Backend Relevance

GC behavior directly impacts:
- Application latency
- CPU usage
- Memory stability

Common GC problems:
- Excessive object creation
- Large objects
- Static references
- Caches without eviction

Good backend design reduces GC pressure instead of trying to control GC.
