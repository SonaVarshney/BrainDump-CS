# Head Dump vs Thread Dump

A short, friendly brain dump for devs trying to untangle memory and thread mysteries in Java apps.

---

## 🧠 Heap Dump  
> “What’s living in my app’s memory right now?”

### 📌 What is it?
A **snapshot of the Java heap memory** at a point in time—think of it as a photo of all the objects in memory.

### 🔍 What's inside?
- Objects and classes loaded in memory
- References between objects
- Memory usage (who's hogging space)

### 🛠️ When to use?
- Suspecting **memory leaks**
- Analyzing **OutOfMemoryError**
- Want to see which objects aren’t getting garbage collected

### 📦 Tools to analyze:
- Eclipse MAT (Memory Analyzer Tool)
- VisualVM
- JProfiler

---

## 🧵 Thread Dump  
> “What are my threads doing right now?”

### 📌 What is it?
A **snapshot of all active threads**, their states, and what they're currently executing.

### 🔍 What's inside?
- Thread names & IDs
- Thread states (RUNNABLE, BLOCKED, WAITING)
- Stack traces showing current code execution
- Lock/monitor info (for deadlocks!)

### 🛠️ When to use?
- Diagnosing **deadlocks** 🧱
- Performance issues (e.g., high CPU usage)
- Checking thread starvation or stuck threads

### 🛠️ Tools to analyze:
- `jstack` (CLI)
- VisualVM
- Java Mission Control

---

## 💡 TL;DR
| Feature       | Heap Dump                       | Thread Dump                     |
|---------------|----------------------------------|----------------------------------|
| Focus         | Memory (objects)                | Threads (execution)             |
| Usage         | Debug memory leaks, OOM errors  | Debug deadlocks, performance    |
| Tools         | MAT, VisualVM, JProfiler        | jstack, VisualVM, JMC           |

---

### 🎉 Bonus Tip:
Got an OOM and high CPU? Take **both** dumps and analyze side-by-side like a debugging ninja 🥷

---
