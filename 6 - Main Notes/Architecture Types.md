
2025-12-17

Tags: [[Programming]] [[Software Engineering]]
# Architecture Types
key design factors:
- Development: Modularity, Testability, Ease of Integration  
- Evolution: Extensibility, Maintainability, Portability  
- Operation: Performance, Security, Ease of Use, Availability

**Architecture Sources**
- Past Experience
- Learning from the ecosystem
- Templates
#### Main Program & Subprograms
This is kind of the "default" application architecture, it has an organized hierarchy of function calls that form a tree. The control flow starts from the main program and there is a single thread of execution.

✓  Simple to understand and debug
✓ Clear program structure
X  Can lead to tight coupling
X  Can be difficult to modify or extend
#### Pipe and Filter
![[Pasted image 20251206185949.png]]
Filters are independent processing units and pipes simply forward the data between filters. This version is step by step and there should be **no** shared state between filters.

✓  Easy to understand and Maintain
✓  High reusability of filters
✓  Good for parallel processing 
X   Can have high latency (?)
X   Not good for interactive applications (?)

#### Data Centered
![[Pasted image 20251206190808.png]]
The central data repository in this case is accessed by multiple different components, some consequences of this is loose coupling between each of the components and the data is independent of applications.

✓ Data consistency and integrity
✓ Easy to add new clients 
✓ Data is independent of applications
X  Single point of failure risk 
X  Can become a performance bottleneck

#### Layered
This version uses an organized hierarchy of responsibility with a strict separation of layers only allowed to call downward. There should also be a loose coupling between layers and abstraction so that the implementation details are hidden.

✓ Easy to develop and maintain
✓ Good for teams (simply parallelizable)
✓ Great for testing
X  Potential performance overhead (?)
X  Can be too rigid for some applications
![[Pasted image 20251206192621.png]]

#### Software Component
A software component is a single, self contained unit of functionality. It encapsulates functionality and data, has a defined interface for access, is modular and reusable, and it hides implementation details.

#### Software Design patterns
Each pattern has a  
- Name
- Problem / when to apply it  
- Solution - design elements & relationships  
- Consequences - benefits & trade-offs  
Why use patterns?  
- Accelerate development  
- Improve design quality  
- Common vocabulary for teams  
- Capture expert knowledge
#### 23 classic design problems

### Service Oriented Architecture
Architecture built around reusable services that represent business capabilities. Idea is to break down monolithic code into interoperable services. The core concepts are service, loose coupling, service contract, and service composition.

# References
[[Software Development Life Cycle (SDLC)]]

[[Performance Measurement & Reliability]]