
2026-06-01

Tags: [[Software Engineering (SWE)]] [[Java]] [[Software Engineering (SWE)]]
# Design patterns- Facade
This pattern provides a simple and unified interface to a complex subsystem. It hides the internal complexity of the system, making it easier to use and maintain. The Facade Pattern achieves this by introducing a facade object that acts as a single entry point.

![[Pasted image 20260601164533.png]]

examples: home automation services provide a single interface to control lighting, heating and security systems. Streaming services offer a single interface for encoding, buffering, and video playback.

**pros:**
 - Simplified Interface: Provides a clear interface while hiding system complexities.
 - Reduced Coupling: Minimizes client dependency on system internals and promotes modularity.
 - Encapsulation: Shields clients from subsystem changes by wrapping complex interactions.
 - Improved Maintainability: Enables easier system changes, refactoring, and extensions without affecting clients.

**cons:**
 - Increased Complexity: Adds another abstraction layer, making code harder to understand and debug.
 - Reduced Flexibility: Limits direct access to specific subsystem functionalities.
 - Overengineering: Can add unnecessary complexity in simple systems.
 - Potential Performance Overhead: Extra indirection may impact performance in critical scenarios.   
# References
- 