## 🧵 How JVM Handles Multithreading

### 🔸 JVM and Threads

- Java **supports multithreading** to fully utilize system resources.
- Multithreading in Java allows **concurrent execution of two or more threads**, improving CPU utilization.

### 🔸 Threads in Java

- A **thread** is the smallest unit of execution, also known as a *lightweight process*.
- Java supports multithreading using:
  - `Thread` class (from `java.lang` package)
  - `Runnable` interface (from `java.lang` package)

### 🔸 When a Java Program Starts

- As soon as a Java program starts, the **JVM creates one thread automatically** — called the **main thread**.
- This main thread is responsible for executing the `main()` method.

```java
System.out.println(Thread.currentThread().getName()); // Output: main
```

### 🔸 JVM’s Role in Managing Threads

- **Single-core system**:
  - JVM + OS together **manage thread switching**.
  - Uses **time slicing** (each thread gets a small time window).
  - It gives an **illusion of parallelism** (since only one thread runs at a time).

- **Multi-core system**:
  - JVM can **distribute threads across multiple cores**.
  - Allows **true parallel execution** of threads.
  - JVM collaborates with the OS scheduler to optimize thread execution.

### 🔸 Summary

| Concept                     | Handled By             | Behavior                               |
|----------------------------|------------------------|----------------------------------------|
| Main thread                | JVM                    | Created automatically on start         |
| Thread scheduling (1 core) | JVM + OS               | Uses time slicing                      |
| Thread scheduling (n cores)| JVM + OS               | True parallel execution possible       |
| Thread creation            | `Thread`, `Runnable`   | Programmer-defined logic               |

