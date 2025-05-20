Reflection in Java is a powerful feature that allows your program to examine and manipulate the internal properties of classes, interfaces, fields, and methods at **runtime**, even if they are private. It’s part of the `java.lang.reflect` package and is commonly used in frameworks, tools, and libraries.

---

##  What is Reflection?

Java Reflection is an **API** that allows:

* Inspecting classes, interfaces, fields, and methods during runtime
* Instantiating objects
* Invoking methods
* Modifying field values

It bypasses compile-time safety checks and allows dynamic behavior.

### Core Classes in `java.lang.reflect`

* `Class<?>` – entry point to reflection (obtained via `Class.forName()` or `obj.getClass()`)
* `Field` – represents a field
* `Method` – represents a method
* `Constructor` – represents a constructor
* `Modifier` – helps check access levels like public, private

---

## Common Reflection Operations

### 1. **Accessing Class Metadata**

```java
Class<?> clazz = Class.forName("java.lang.String");
System.out.println(clazz.getName()); // prints "java.lang.String"
```

### 2. **Getting Class Fields**

```java
Field[] fields = clazz.getDeclaredFields();
for (Field field : fields) {
    System.out.println(field.getName());
}
```

### 3. **Getting Class Methods**

```java
Method[] methods = clazz.getDeclaredMethods();
for (Method method : methods) {
    System.out.println(method.getName());
}
```

### 4. **Creating an Object Dynamically**

```java
Class<?> c = Class.forName("java.lang.StringBuilder");
Constructor<?> cons = c.getConstructor();
Object obj = cons.newInstance();
```

### 5. **Invoking a Method Dynamically**

```java
Method appendMethod = obj.getClass().getMethod("append", String.class);
appendMethod.invoke(obj, "Hello");
System.out.println(obj.toString()); // prints "Hello"
```

### 6. **Accessing/Modifying Private Fields**

```java
Field privateField = obj.getClass().getDeclaredField("value");
privateField.setAccessible(true);
privateField.set(obj, new char[]{'J','a','v','a'});
```

---

## Use Cases of Reflection

### 1. **Frameworks (Spring, Hibernate)**

* Spring uses reflection to instantiate beans and inject dependencies.
* Hibernate uses it to map database columns to fields in Java objects.

### 2. **Dependency Injection**

Reflection enables classes to be dynamically created and injected at runtime.

### 3. **Serialization/Deserialization**

Libraries like Jackson and Gson use reflection to access fields for reading and writing JSON/XML.

### 4. **Testing Frameworks (JUnit)**

JUnit uses reflection to invoke methods annotated with `@Test` even if private.


## Limitations

* **Performance Overhead** – Slower than direct code due to type checks and security checks.
* **Security Risk** – Can break encapsulation and access private members.
* **No Compile-Time Checks** – Errors may only show up at runtime.
* **Use with Caution** – Especially in production environments.

---

## When Should You Use Reflection?

| Use Reflection When…                            | Avoid When…                              |
| ----------------------------------------------- | ---------------------------------------- |
| Building frameworks or libraries                | You can achieve the same via normal OOP  |
| Dynamic behavior is needed                      | It complicates the code unnecessarily    |
| Runtime inspection or modification is essential | You need strict performance and security |

---



##  Breaking the Singleton Pattern (Reflection Pitfall)

### How Singleton Works

Singleton ensures that only **one instance** of a class is ever created:

```java
public class Singleton {
    private static final Singleton instance = new Singleton();
    private Singleton() {}  // private constructor
    public static Singleton getInstance() {
        return instance;
    }
}
```

### How Reflection Breaks It

Reflection allows access to the **private constructor**, so you can create **multiple instances**:

```java
import java.lang.reflect.Constructor;

public class BreakSingleton {
    public static void main(String[] args) throws Exception {
        Singleton s1 = Singleton.getInstance();

        Constructor<Singleton> constructor = Singleton.class.getDeclaredConstructor();
        constructor.setAccessible(true); // bypass private
        Singleton s2 = constructor.newInstance(); // second instance

        System.out.println(s1 == s2); // false
    }
}
```

###  Output:

```
false
```

This defeats the entire purpose of the singleton pattern.

---

##  How to Protect Singleton from Reflection

### Using Enum

The best way is to use an `enum`, which is **reflection-proof**:

```java
public enum SafeSingleton {
    INSTANCE;
}
```

Java ensures that enum constructors are protected from reflection attacks.

---


