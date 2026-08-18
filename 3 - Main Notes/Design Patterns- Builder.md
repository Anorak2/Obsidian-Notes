
2026-05-29

Tags: [[Java]] [[Software Engineering (SWE)]] [[OOP Design Patterns]]
# Design Patterns- Builder
This is a creational pattern that provides a step by step way to create a complex object. It separates the construction process from the object’s representation, enabling the same method to create different variations of an object. 

examples: SQL query builders, UI component builders, Document Builders, String Builders.

**Components:**
- Product: The complex object being constructed, typically a class with attributes representing different parts built by the Builder.
- Builder: An interface or abstract class that defines construction steps, including methods to build individual parts of the product.
- Concrete Builder: Implements the Builder interface, providing specific logic to construct each part and create a particular variation of the product.
- Director: Manages the construction process by working with a Builder, without knowing the internal details of how parts are created.
- Client: Initiates the construction by creating a Builder and passing it to the Director to build the final product.


## Example Code
![[Pasted image 20260529192457.png]]
```java
// Product
class Computer {
    private String cpu;
    private String ram;
    private String storage;

    public void setCPU(String cpu) { this.cpu = cpu; }

    public void setRAM(String ram) { this.ram = ram; }

    public void setStorage(String storage) {
        this.storage = storage;
    }

    public void displayInfo() {
        System.out.println("Computer Configuration:\n"
                           + "CPU: " + cpu + "\n"
                           + "RAM: " + ram + "\n"
                           + "Storage: " + storage + "\n");
    }
}

// Builder interface
interface Builder {
    void buildCPU();
    void buildRAM();
    void buildStorage();
    Computer getResult();
}

// ConcreteBuilder
class GamingComputerBuilder implements Builder {
    private Computer computer = new Computer();

    public void buildCPU() {
        computer.setCPU("Gaming CPU");
    }

    public void buildRAM() { computer.setRAM("16GB DDR4"); }

    public void buildStorage() {
        computer.setStorage("1TB SSD");
    }

    public Computer getResult() { return computer; }
}

// Director
class ComputerDirector {
    public void construct(Builder builder) {
        builder.buildCPU();
        builder.buildRAM();
        builder.buildStorage();
    }
}

// Client
public class Main {
    public static void main(String[] args) {
        GamingComputerBuilder gamingBuilder
            = new GamingComputerBuilder();
        ComputerDirector director = new ComputerDirector();
        director.construct(gamingBuilder);
        Computer gamingComputer = gamingBuilder.getResult();
        gamingComputer.displayInfo();
    }
}
```
# References
- 