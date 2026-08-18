
2026-07-12

Tags: [[Performance Measurement & Reliability]] [[Designing Data Intensive Applications]]
# What is Maintainability
This is a difficult term to describe, but generally the following key points are sufficient:
- Operability. Make it easy for operations teams to keep the system running smoothly.
- Simplicity. Make it easy for new engineers to understand the system, by removing as much complexity as possible from the system. 
- Plasticity. Make it easy for engineers in future to make changes to the system, adapting it for unanticipated use cases as requirements change. 

## Operability
**Systems aiming to make operations easier should:**
- make it easy to do routine tasks
- provide visibility into the runtime behavior and internals of the system with good monitoring;
- provide support for automation and integration with standard tools
- avoid dependency on individual machines (allowing machines to be taken down for maintenance while the system as a whole continues running uninterrupted)
- good documentation and an easy-to-understand operational model (“if I do X, Y will happen”)
- good default behavior, but also giving administrators the freedom to override defaults when needed
- self-healing where appropriate, but also giving administrators manual control over the system state when needed
- predictable behavior, minimizing surprises

## Simplicity
**Abstractions** are one of the best tools available for reducing complexity in large systems, and a lot of code can be hidden behind a good facade. Good abstractions can be hard to find, and it worth paying attention to good reusable components.

## Evolvability
The ease with which you can modify a data system, and adapt it to changing requirements, is closely linked to its simplicity and its abstractions: simple and easy-to understand systems are usually easier to modify than complex ones.

# References
- [[Design patterns- Facade]]