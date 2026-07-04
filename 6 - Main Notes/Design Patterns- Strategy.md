
2026-06-03

Tags: [[OOP Design Patterns]] [[Java]] [[Software Engineering (SWE)]]
# Design Patterns- Strategy
The Strategy Design Pattern is a behavioral pattern that defines a group of related algorithms, encapsulates each one in a separate class, and makes them interchangeable. It allows the algorithm to vary independently from the client that uses it, enabling behavior changes at runtime without altering existing code. The key here is that there are different ways to solve the problem, but that each of the strategies has to solve the same problem.

- Encapsulates different algorithms into separate strategy classes, allowing dynamic selection or switching at runtime.
- Promotes flexibility by reducing complex conditional logic and making code easier to maintain.

Examples: A payment system where a user (client) selects a payment method, and the system (context) applies a strategy like Credit Card, UPI, or PayPal to process the payment. When different algorithms may be required, with some easy examples including sorting and compression algorithms.


**pros:**
 - Promotes open/closed principle by allowing new strategies to be added easily
 - Makes code cleaner and easier to maintain
 - Enables runtime behavior changes without code modification

**cons:**
 - Increases the number of classes and objects in the system.
 - Clients need to understand and select the appropriate strategy implementation.
 - May cause slight performance overhead due to extra object creation and method calls.

# References
- 