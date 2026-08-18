
2026-05-29

Tags: [[Software Engineering (SWE)]] [[Java]] [[Software Engineering (SWE)]]
# Design Pattern- Factory
The factory design pattern is a very common OOP creational pattern. It works by defining an interface for creating objects on the parent level, and subclasses can then override these methods. The key here is that because subclasses override the factory methods there is flexible object creation, and it allows for improved maintainability and adaptability. A simple real world analogy is placing an order at a restaurant to a waiter who then takes it to the kitchen and decides who prepares it.

![[Pasted image 20260529123216.png]]

**Component**
- Creator: This is an abstract class or an interface that declares the factory method. The creator typically contains a method that serves as a factory for creating objects. It may also contain other methods that work with the created objects.
- Concrete Creator: Concrete Creator classes are subclasses of the Creator that implement the factory method to create specific types of objects.
- Product: This is the interface or abstract class for the objects that the factory method creates. The Product defines the common interface for all objects that the factory method can create.
- Concrete Product: Concrete Product classes are the actual objects that the factory method creates. Each Concrete Product class implements the Product interface or extends the Product abstract class.

**Pros:**
- Encapsulates object creation logic
- Promotes loose coupling by depending on abstractions instead of concrete classes.
- Allows new product types without modifying existing code.
- Improves reusability and maintainability by centralizing and reusing creation logic.

**Cons:**
- introduces complexity
- adds more classes, I mean look at the number of classes in the example below
- unnecessary for many small or simple applications
## Examples
![[Pasted image 20260529123908.png]]

examples: Android OS activities, payment gateways for spawning payment type, game development for NPC, item, or enemy creation.



# References
- 