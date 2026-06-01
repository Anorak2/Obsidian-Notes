
2026-05-29

Tags: [[Software Engineering (SWE)]] [[Java]] [[OOP Design Patterns]]
# Design Pattern- Abstract Factory
The Abstract Factory Pattern is a creational design pattern that provides an interface for creating families of related or dependent objects without specifying their concrete classes. This means that it is basically a factory factory.
![[Pasted image 20260529184135.png]]

Components:
- abstract factory that provides a common interface for the concrete factories
- concrete factories implement the rules specified by the abstract factory
- abstract products is an abstract or interface that all concrete products must use in order to be interchangeable
- concrete products adhere to the abstract product in a way consistent with the family or category
- Client utilizes the abstract factory to create families of objects without specifying their concrete types and interacts with objects through abstract interfaces provided by abstract products

**Pros**
- The Abstract Factory Pattern improves modularity, flexibility, and scalability in large systems.
- Promotes loose coupling between client and product classes.
- Makes switching product families easy without modifying client code.
- Supports Open/Closed Principle.

**Cons**
- Increases number of classes and interfaces.
- Can make the system more complex than necessary for small projects.
- Adding a new product type requires modifying the abstract factory interface.
# References
- [[Design Pattern- Factory]]
- [[SOLID design principles | Open-Closed Principle]]
- 