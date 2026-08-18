
2026-05-28

Tags: [[Software Engineering (SWE)]] [[Java]] [[OOP Design Patterns]]
# Design Pattern- Singleton
The Singleton Design Pattern ensures that a class has only one instance and provides a global access point to it. It is used when we want centralized control of resources, such as managing database connections, configuration settings or logging.

This prevents accidentally creating multiple instances and ensures that limited resources like memory and connections are managed efficiently. This pattern also simplifies coordination across different parts of the application since there is a single shared instance.

Examples: Logging systems, configuration managers, database connections, thread pools

```java
// Static member to hold the single instance
private static Singleton instance;

// Static factory method for global access
public static Singleton getInstance()
{
    // Check if an instance exists
    if (instance == null) {
        // If no instance exists, create one
        instance = new Singleton();
    }
    // Return the existing instance
    return instance;
}
```
### Lazy Initialization
```java
class Singleton {
    private static Singleton obj;

    // private constructor to force use of getInstance() to create Singleton object
    private Singleton() {}
    public static Singleton getInstance()
    {
        if (obj == null)
            obj = new Singleton();
        return obj;
    }
}
```

### Threadsafe
```java
class Singleton {
    private static Singleton obj;
    private Singleton() {}

    // Only one thread can execute this at a time
    public static synchronized Singleton getInstance()
    {
        if (obj == null)
            obj = new Singleton();
        return obj;
    }
}
```

# References
-  [[Design Pattern- Static Factory]]