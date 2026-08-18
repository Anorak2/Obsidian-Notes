
2026-07-01

Tags: [[Software Engineering (SWE)]] [[Java]]
# Design pattern- Model View Controller (MVC)
The MVC (Model–View–Controller) design pattern divides an application into three separate components: Model, View, and Controller. This separation of concerns improves code organization, maintainability, and scalability. Each component handles a specific responsibility, making the application easier to modify and extend.

- Model: Manages application data and business logic.
- View: Handles the user interface and presentation of data.
- Controller: Processes user input and coordinates between Model and View.

![[Pasted image 20260701144127.png]]

**Why?**
MVC is used to organize an application by separating responsibilities, making development and maintenance easier.
 - Allows independent development and modification of Model, View, and Controller.
 - Improves maintainability by isolating changes to specific components.
 - Simplifies testing by separating business logic from the user interface.
 - Supports scalability and smoother addition of new features.

Practically speaking, the MVC pattern allows you to choose between strategies (see the strategy design pattern) at every transition between layers. This makes it very easy to swap the output (view) from HTML to JSON/XML if you are supporting both a web application and a desktop application 


**Pros**
- Clear separation of concerns improves maintainability.
- Allows parallel development of UI and business logic.
- Makes testing easier, especially unit testing.

**Cons**
- Increased complexity for small or simple applications.
- Requires more initial design and planning.
- Can be harder for beginners to understand and implement.
# References
- [[Design Patterns- Strategy]]