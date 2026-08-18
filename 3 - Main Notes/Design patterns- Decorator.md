
2026-06-01

Tags: [[Software Engineering (SWE)]] [[Java]] [[Software Engineering (SWE)]]
# Design patterns- Decorator
This pattern lets you dynamically add behavior to individual objects without changing other objects of the same class. It uses decorator classes to wrap concrete components, making functionality more flexible and reusable.

![[Pasted image 20260601162941.png]]

examples: Video streams can have decorators such as subtitles and audio options, using a decorator the base option is unchanged. Text processors allow for bold, italic, and underline. Java I/O streams such as `FileInputStream` can be wrapped with `BufferedInputStream` or `DataInputStream`.

**pros:**
- Improves flexibility by allowing behavior to be added or removed at runtime.
- Promotes Single Responsibility Principle, as functionality can be divided among classes.
- Avoids the use of large subclasses that combine multiple behaviors.

**cons:**
- Can make the system more complex due to many small decorator classes.
- Debugging and understanding the flow of decorated objects may be harder.
- Overuse can lead to code that is difficult to maintain.

# References
- 