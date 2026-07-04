
2026-06-01

Tags: [[OOP Design Patterns]] [[Java]] [[Software Engineering (SWE)]]
# Design patterns- Adapter
Adapter Design Pattern is a structural pattern that acts as a bridge between two incompatible interfaces, allowing them to work together. It is especially useful for integrating legacy code or third-party libraries into a new system. It can be either through a  Class Adapter (using inheritance) and Object Adapter (using composition).

![[Pasted image 20260601161814.png]]

In this example Specific Request doesn't match the format for Request, so the adapter acts as a middleman to convert the request into the proper interface.

examples: Software that allows different file formats such as CSV, JSON, XML, etc. Device Drivers, Database connectors, and Language Converters. If there are dramatic API changes it may be easier to use adapters than to rewrite all of the old code.

**components**
- Target Interface: The interface expected by the client, defining the operations it can use.
- Adaptee: The existing class with an incompatible interface that needs integration.
- Adapter: Implements the target interface and uses the adaptee internally, acting as a bridge.
- Client: Uses the target interface, unaware of the adapter or adaptee details.


**pros:**
 - Promotes code reuse without modification, as well as preventing code duplication
 - Keeps classes focused on core logic by isolating adaptation.
 - Supports multiple interfaces through interchangeable adapters.
 - Decouples system from implementations, easing modifications and swaps.

**cons:**
 - Adds complexity and can make code harder to follow.
 - Introduces slight performance overhead due to extra indirection, potentially could add up.
 - Multiple adapters increase maintenance effort.
 - Handling many interfaces may require multiple adapters, complicating design.

## Simple Code Example

```java
// Target Interface
interface Printer {
    void print();
}

// Adaptee
class LegacyPrinter {
    public void printDocument() {
        System.out.println("Legacy Printer is printing a document.");
    }
}

// Adapter
class PrinterAdapter implements Printer {
    private LegacyPrinter legacyPrinter = new LegacyPrinter();
    @Override
    public void print() {
        legacyPrinter.printDocument();
    }
}

// Client Code
public class Client {
    public static void clientCode(Printer printer) {
        printer.print();
    }
    public static void main(String[] args) {
        // Using the Adapter
        PrinterAdapter adapter = new PrinterAdapter();
        clientCode(adapter);
    }
}
```

# References
- 