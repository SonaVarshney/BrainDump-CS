## 🧵 Creating Threads in Java

In Java, you can create a new thread using two primary methods:

---

#### ✅ Method 1: Extending the `Thread` class

```java
class MyThread extends Thread {
    @Override
    public void run() {
        // Code to run in new thread
        for (int i = 0; i < 10000; i++) {
            System.out.println("World");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start(); // Starts new thread

        for (int i = 0; i < 10000; i++) {
            System.out.println("Hello");
        }
    }
}
```

🔹 `start()` → calls the overridden `run()` method in a new thread.  
🔹 Output appears in **random order** (no sequential guarantee).

---

#### ✅ Method 2: Implementing `Runnable` interface

```java
class MyRunnable implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 10000; i++) {
            System.out.println("World");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        MyRunnable r = new MyRunnable();
        Thread t1 = new Thread(r); // Pass Runnable to Thread constructor
        t1.start(); // Starts new thread

        for (int i = 0; i < 10000; i++) {
            System.out.println("Hello");
        }
    }
}
```

🔹 Useful when your class already extends another class (Java doesn't support multiple inheritance).

---

### ℹ️ Notes

- `Thread.currentThread().getName()` → returns the name of the current thread. (main/Thread-0 etc)
- Threads run independently. There is **no fixed order** in which "Hello" and "World" will be printed.
- Avoid using infinite loops without care — they can block execution and cause compilation errors (e.g., unreachable code).
