
## 🔐 Reentrant Locks 

---

### 🚀 What is a Lock?

* A lock is a synchronization aid that allows only one thread to access a critical section (shared resource) at a time.
* Java’s intrinsic locking (`synchronized`) is simpler but less flexible.

---

### 🔁 What is a Reentrant Lock?

* A **Reentrant Lock** (also known as a recursive lock) **allows the thread that currently holds the lock to re-acquire it without getting blocked**.
* It tracks how many times it has been acquired by the same thread and requires that many `unlock()` calls.

> 🧠 Think of it like a door that lets you in multiple times if you already have the key — but you must exit as many times as you entered.

---

### ✅ Why Use ReentrantLock over `synchronized`?

| Feature                | `synchronized`   | `ReentrantLock`            |
| ---------------------- | ---------------- | -------------------------- |
| Try to acquire?        | ❌ No             | ✅ `tryLock()`              |
| Timeout to acquire?    | ❌ No             | ✅ `tryLock(timeout)`       |
| Interruptible lock     | ❌ No             | ✅ `lockInterruptibly()`    |
| Fairness policy        | ❌ No             | ✅ Optional fairness        |
| Explicit unlock needed | ❌ No (automatic) | ✅ Yes (must call `unlock`) |

---

### 🧱 Basic Syntax

```java
import java.util.concurrent.locks.ReentrantLock;

ReentrantLock lock = new ReentrantLock();

lock.lock();      // Acquires the lock
try {
    // critical section
} finally {
    lock.unlock();  // Always release in finally block
}
```

---

### 🔄 Reentrancy Example

```java
class MyService {
    private final ReentrantLock lock = new ReentrantLock();

    public void outer() {
        lock.lock();
        try {
            inner();  // Same thread can acquire again
        } finally {
            lock.unlock();
        }
    }

    public void inner() {
        lock.lock();  // Reentrant acquisition
        try {
            // do something
        } finally {
            lock.unlock();  // Must unlock same number of times as locked
        }
    }
}
```

---

### ⏱️ Try Lock and Timeout

```java
if (lock.tryLock()) {
    try {
        // critical section
    } finally {
        lock.unlock();
    }
} else {
    // Couldn’t get the lock
}
```

```java
if (lock.tryLock(5, TimeUnit.SECONDS)) {
    try {
        // Got the lock
    } finally {
        lock.unlock();
    }
} else {
    // Timeout
}
```

---

### 🧵 lockInterruptibly()

Used when a thread needs to respond to an interrupt while waiting for a lock.

```java
try {
    lock.lockInterruptibly();
    try {
        // critical section
    } finally {
        lock.unlock();
    }
} catch (InterruptedException e) {
    // Handle interrupt
}
```

---

### 🎯 Fairness Policy

```java
ReentrantLock fairLock = new ReentrantLock(true); // Fair lock

// Ensures first-come-first-served order
```

* `false` (default): Unfair, may favor throughput.
* `true`: Fair, avoids thread starvation.

---

### 🧮 Count of Hold

```java
lock.getHoldCount(); // Number of times current thread has locked it
lock.isHeldByCurrentThread(); // Check ownership
lock.isLocked(); // Is lock currently held?
```

---

### ⚠️ Best Practices

1. Always **unlock in a finally block**.
2. Avoid **holding a lock during I/O**, long operations.
3. Don't forget **unlock for each lock**, especially in reentrant scenarios.
4. Prefer **`tryLock()`** in high-contention areas to avoid deadlock.
5. Avoid nested locks if possible (can cause deadlocks).

---

### 🧰 Handy Real-World Use Cases

* **Thread-safe singletons** (with lazy initialization)
* **Complex concurrent workflows** (e.g., producer-consumer)
* **Manual deadlock handling**
* **Custom synchronizers** (e.g., read-write locks, barriers)

---

### 📌 Quick Summary (Revision Notes)

| Concept             | Description                                  |
| ------------------- | -------------------------------------------- |
| Reentrant?          | Yes, same thread can lock multiple times     |
| Unlock needed?      | Yes, same number of times as locked          |
| tryLock()?          | Returns immediately or waits with timeout    |
| Fairness supported? | Yes, configurable in constructor             |
| Replacement for?    | Advanced alternative to `synchronized` block |
| Exception safety?   | Use `try-finally` for safe unlock            |

---
