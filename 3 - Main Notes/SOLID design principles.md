
2026-05-29

Tags: [[Java]] [[OOP Design Patterns]] [[Software Engineering (SWE)]]
# SOLID design principles
The solid principles are a set of design guidelines popularized by Uncle Bob in the early 2000's.

The principles are 
- Single Responsibility Principle
- Open/Closed Principle
- Liskov Substitution Principle
- Interface Segregation Principle
- Dependency Injection Principle

## Single Responsibility Principle
The single responsibility principle states that a class, module, or function should have only one reason to change, meaning it should do one thing.

For example, a class that shows the name of an animal should not be the same class that displays the kind of sound it makes and how it feeds.
## Open Closed Principle
The open-closed principle states that software entities (classes, modules, functions, and so on) should be open for extension, but closed for modification. What this means is that it should be easy to add new functionalities without having to change existing code.
## Liskov Substitution Principle
The principle states that child classes or subclasses must be substitutable for their parent classes or super classes. In other words, the child class must be able to replace the parent class. This has the advantage of letting you know what to expect from your code.
## Interface Segregation Principle
The interface segregation principle states that clients should not be forced to implement interfaces or methods they do not use. Specifically this means large interfaces should be broken down into smaller interfaces so that clients only need to depend on relevant interfaces. This makes codebases easier to maintain.
## Dependency Inversion Principle
The dependency inversion principle is about decoupling software modules. That is, making them as separate from one another as possible. This means instead of writing code that relies on specific details of how lower-level code works, you should write code that depends on more general abstractions that can be implemented in different ways.
![[Pasted image 20260529191050.png]]
In this example the presenter says that the problem is the new keyword 

# References
- 