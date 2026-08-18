2026-06-11

Tags: [[Databases]] [[Java]]
# Object Relational Mapping (ORM)
Fundamentally an ORM tool is designed to fix a common mismatch between how data is typically stored and how data is typically handled. If data is stored in relational tables, but is typically used in an object oriented language then to store an object there needs to be a mapping layer between the two. Frameworks such as ActiveRecord and Hibernate exist in order to reduce this boilerplate code, but even these frameworks aren't perfect.

**Pros**
- Clear separation of concerns improves maintainability.
- Allows parallel development of UI and business logic.
- Makes testing easier, especially unit testing.

**Cons**
- Increased complexity for small or simple applications.
- Requires more initial design and planning.
- Can be harder for beginners to understand and implement.


# References
- [[Relational Database Model]]