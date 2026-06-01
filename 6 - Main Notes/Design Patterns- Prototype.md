
2026-05-30

Tags: [[Java]] [[Software Engineering (SWE)]] [[OOP Design Patterns]]
# Design Patterns- Prototype
The prototype pattern is required when object creation is a time-consuming, and costly operation, so we create objects with the existing object itself  by copying the existing ones. The cloned object can modify only the required properties, avoiding unnecessary changes to the original object.

![[Pasted image 20260530154738.png]]
For example here you could clone a Mage and then only change the name and level.


**Components**
- Prototype Interface / Abstract Class: Defines the clone() method and sets a standard for all objects that can be cloned.
- Concrete Prototype: Implements the prototype interface or extends the abstract class to provide actual cloning behavior.
- Client: Uses the prototype to create new objects by calling the clone() method.
- Clone Method: Specifies how an object is copied and is implemented by concrete prototypes.

**Pros:**
 - Simplifies object creation process.
 - Reduces subclassing for different object configurations since existing configs can be tweaked. 
 - Allows dynamic addition or removal of object types at runtime.
 - Promotes flexibility in cloning and modifying objects.

**Cons**
 - Cloning complex objects can be difficult.
 - Deep copy implementation can be complicated.
 - Requires careful handling of references to avoid shared state issues.
 - Every class must implement cloning logic properly.
## Code Example
```java
// Prototype interface
interface Shape {
    Shape clone();  // Make a copy of itself
    void draw();    // Draw the shape
}

// Concrete prototype
class Circle implements Shape {
    private String color;
    // When you create a circle, you give it a color.
    public Circle(String color) {
        this.color = color;
    }
    // This creates a copy of the circle.
    @Override
    public Shape clone() {
        return new Circle(this.color);
    }
    // This is how a circle draws itself.
    @Override
    public void draw() {
        System.out.println("Drawing a " + color + " circle.");
    }
}

// Client code
class ShapeClient {
    private Shape shapePrototype;
	
    // When you create a client, you give it a prototype (a shape).
    public ShapeClient(Shape shapePrototype) {
        this.shapePrototype = shapePrototype;
    }

    // This method creates a new shape using the prototype.
    public Shape createShape() {
        return shapePrototype.clone();
    }
}

// Main class
public class PrototypeExample {
    public static void main(String[] args) {
        // Create a concrete prototype (a red circle).
        Shape circlePrototype = new Circle("red");

        // Create a client and give it the prototype.
        ShapeClient client = new ShapeClient(circlePrototype);

        // Use the prototype to create a new shape (a red circle).
        Shape redCircle = client.createShape();

        // Draw the newly created red circle.
        redCircle.draw();
    }
}
```

# References
- 