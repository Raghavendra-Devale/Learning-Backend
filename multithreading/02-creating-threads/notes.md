# Multithreading – Lesson 2  
## Creating Threads in Java

These notes explain how threads are created in Java, the difference between `run()` and `start()`, and why `Runnable` is preferred over extending `Thread`.

---

## 1. What Does Creating a Thread Mean?

Creating a thread means:
- JVM requests the OS to create a new execution path
- A new stack is allocated
- The thread is scheduled independently

Calling a method alone does NOT create a thread.

---

## 2. run() vs start() (Very Important)

### run()
- Executes like a normal method
- Runs on the current thread
- Does NOT create a new thread

### start()
- Creates a new thread
- JVM calls run() internally
- Executes concurrently

Calling `run()` directly does not start a new thread.

---

## 3. Why start() Is Important

- start() is responsible for thread creation
- It interacts with OS-level threading
- It sets up thread lifecycle and state

Only `start()` creates concurrency.

---

## 4. Ways to Create Threads

### Option 1: Extending Thread
```java
class MyThread extends Thread {
    public void run() {
        // task
    }
}
````

### Option 2: Implementing Runnable

```java
class MyTask implements Runnable {
    public void run() {
        // task
    }
}
new Thread(new MyTask()).start();
```

Both work, but design quality differs.

---

## 5. Why Extending Thread Is Discouraged

Problems:

* Java supports single inheritance
* Task logic tightly coupled to thread
* Harder to reuse and test
* Poor separation of concerns

Extending Thread mixes *what to do* with *how to execute*.

---

## 6. Why Runnable Is Preferred

Runnable represents:

* The task to execute
* Independent of execution mechanism

Benefits:

* Loose coupling
* Reusable tasks
* Can be executed by threads or thread pools

Modern Java concurrency is built on Runnable.

---

## 7. Thread Lifecycle Limitation

* A thread can be started only once
* After execution, it enters TERMINATED state
* Restarting a thread throws IllegalThreadStateException

Threads are single-use objects.

---

## 8. Backend Best Practice

* Avoid manual thread creation
* Use Runnable with ExecutorService
* Understand this model before using thread pools

---

## 9. Interview-Safe Summary

> “Calling start() creates a new thread and invokes run() internally. Runnable is preferred over extending Thread because it separates task from execution and avoids tight coupling.”




