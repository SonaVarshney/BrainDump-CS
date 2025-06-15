### ✅ What Are Annotations in Java?

**Annotations** in Java are metadata (information) about the code. They don’t change how the program runs but can be used by the compiler, development tools, or frameworks at runtime to apply certain behavior.

#### 📌 Syntax:

```java
@AnnotationName
```

#### 📌 Example:

```java
@Override
public String toString() {
    return "Example";
}
```

Here, `@Override` tells the compiler that the method overrides a method in the superclass.

---

### 🔍 Custom Annotations in Java

You can create your own annotations using `@interface`.

#### 📌 Basic Custom Annotation:

```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface WithLock {
}
```

* `@Retention(RetentionPolicy.RUNTIME)`: Makes the annotation available at runtime using reflection.
* `@Target(ElementType.METHOD)`: Means this annotation can only be used on methods.

---

## 🔐 ReentrantLock + Annotation-Based Locking

Now, let's say you want to create an annotation to **automatically handle locking and unlocking** around a method using `ReentrantLock`.

This cannot be done **purely at compile-time** because Java annotations don’t inject behavior by themselves — **you need a proxy or aspect-oriented programming (AOP)** tool like **AspectJ** or **Spring AOP**.

---

### ✅ Full Example Using Plain Java + Reflection

**Step 1: Define the Annotation**

```java
import java.lang.annotation.*;

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface WithLock {
}
```

---

**Step 2: Business Class with Lock**

```java
import java.util.concurrent.locks.ReentrantLock;

public class MyService {
    private final ReentrantLock lock = new ReentrantLock();

    @WithLock
    public void criticalSection() {
        System.out.println("Inside critical section");
    }

    public ReentrantLock getLock() {
        return lock;
    }
}
```

---

**Step 3: Invoke Methods with Lock Handling**

```java
import java.lang.reflect.Method;

public class LockHandler {
    public static void invokeWithLock(Object target, String methodName) throws Exception {
        Method method = target.getClass().getMethod(methodName);
        if (method.isAnnotationPresent(WithLock.class)) {
            ReentrantLock lock = ((MyService) target).getLock();
            lock.lock();
            try {
                method.invoke(target);
            } finally {
                lock.unlock();
            }
        } else {
            method.invoke(target);
        }
    }

    public static void main(String[] args) throws Exception {
        MyService service = new MyService();
        invokeWithLock(service, "criticalSection");
    }
}
```

---

### 🧠 Limitations of Manual Reflection Approach

* You have to call the method via `invokeWithLock`, not directly.
* Doesn’t scale well for complex classes.

---

### ✅ Advanced Approach: Spring AOP

With **Spring AOP**, you can define an annotation like `@WithLock` and automatically intercept any method annotated with it to manage locking.

---

### 🧪 Conclusion

* **Annotations** are metadata and don’t change runtime behavior on their own.
* To **apply behavior** like locking, combine annotations with **reflection**, **proxies**, or **AOP**.
* You can simulate this in plain Java, but frameworks like **Spring** make it clean and scalable.



---
---

## ✅ Step-by-Step: Spring AOP Version

---

### 🧱 Step 1: Add Required Dependencies

In your `pom.xml` (for Maven):

```xml
<dependencies>
    <!-- Spring Boot Starter for AOP -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-aop</artifactId>
    </dependency>

    <!-- Optional: Starter for Web/Beans -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter</artifactId>
    </dependency>
</dependencies>
```

---

### 🏷️ Step 2: Create the Custom Annotation

```java
import java.lang.annotation.*;

@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface WithLock {
}
```

---

### 🧠 Step 3: Create a Service with a Lock

```java
import org.springframework.stereotype.Service;
import java.util.concurrent.locks.ReentrantLock;

@Service
public class MyService {
    private final ReentrantLock lock = new ReentrantLock();

    public ReentrantLock getLock() {
        return lock;
    }

    @WithLock
    public void criticalTask() {
        System.out.println("Executing critical task by " + Thread.currentThread().getName());
    }
}
```

---

### 👁️ Step 4: Create the Aspect That Handles Locking

```java
import org.aspectj.lang.ProceedingJoinPoint;
import org.aspectj.lang.annotation.*;
import org.springframework.stereotype.Component;

import java.util.concurrent.locks.ReentrantLock;

@Aspect
@Component
public class LockAspect {

    @Around("@annotation(WithLock)")
    public Object aroundLockedMethods(ProceedingJoinPoint pjp) throws Throwable {
        Object target = pjp.getTarget();

        if (target instanceof MyService) {
            ReentrantLock lock = ((MyService) target).getLock();
            lock.lock();
            try {
                return pjp.proceed(); // run the method
            } finally {
                lock.unlock();
            }
        } else {
            // default behavior if lock not found
            return pjp.proceed();
        }
    }
}
```

---

### 🚀 Step 5: Main Application to Run It

```java
import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.EnableAspectJAutoProxy;

@SpringBootApplication
@EnableAspectJAutoProxy
public class LockDemoApplication implements CommandLineRunner {

    private final MyService service;

    public LockDemoApplication(MyService service) {
        this.service = service;
    }

    public static void main(String[] args) {
        SpringApplication.run(LockDemoApplication.class, args);
    }

    @Override
    public void run(String... args) {
        // run criticalTask with multiple threads
        Runnable task = () -> service.criticalTask();

        Thread t1 = new Thread(task);
        Thread t2 = new Thread(task);

        t1.start();
        t2.start();
    }
}
```

---

## ✅ Output:

Even with multiple threads, only one thread at a time will execute `criticalTask()` because the **lock is automatically applied via AOP**, thanks to the `@WithLock` annotation.

---

### 🧼 Benefits:

* You don't repeat lock/unlock code.
* Behavior is separated cleanly.
* Easy to apply to many methods.

---

