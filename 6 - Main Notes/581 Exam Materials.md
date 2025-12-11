
## Meta
---
 - 
 - since the last test was on october 6th slides 7-11 are fair game
 - if weighted similar to the other exams I'd expect it to be worth 9-12 percent (52 vs 72 points)
 
**topics in the slides + (total raw slides)**
- Finite State machines and state modeling (75 slides)
- architectural design and design types, ex layered and data centered (73 slides)
- software quality and testing (31 slides)
- data flow testing (38 slides)
- SE history / ethics (19 slides)
	- pay extra attention to the eight ACM/IEEE principles

# 07 - FSM and Modeling
--- 
Why FSM?
- Used for modeling a system (or an object) behavior as a set of states it will have
- The states represent the object’s reaction to events
- Upon an event, a system (object) may stay in the same state or make a transition to another state
terms:
- State. A situation during the life of an object during which it satisfies some condition, performs some action, or waits for some event
- Transition is moving from one state to another, 
- Actions. An action is a function that takes an insignificant amount of time to perform, these can happen when a transition is taken, a state is entered, or a state is exited

**Acceptors** return a true and false based on the state the FSM is when it exits

# 08 - Architecture
--- 
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
# 09 - Quality and Testing
--- 
Common SDLC has the problem where testing occurs only at the very end, which can be problematic. We can help fix this with Software Quality Analysis (SQA) which focuses on the entire SDLC and is proactive rather than reactive.

**Formal Verification** uses mathematical proofs to rigorously prove correctness for all cases without testing being necessary. This process is complex and expensive, and therefore only really used in safety critical systems or for very critical pieces of software (you may formally prove the validity of a compiler for example)

**Test Driven development** is the process of writing a representative test case that fails first, and then writing the code to pass the test case afterwards

**Pair Programming** is where there are two developers on the same keyboard and one does the micro and one does the macro

# 10 - Data Flow Testing
---
generate the [[Control Dependence Graph (CDG) and Data Dependence Graph (DDG)|ddg]] and assign each variable in each node with a letter marking what was done to it, d is for defined, k is for killed, and u is for used. he argues that it doesn't make sense to define two in a row without use or to define and kill without use etc.
#  11 - SE History / Ethics
---
![[image-72352d55-88fa-43e6-81de-581ef5266150.png]]