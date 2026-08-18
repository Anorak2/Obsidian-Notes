
2026-05-28


Tags: [[Languages]]
# Java Modules
## Classes
Classes are the OOP primitives that are able to give encapsulation, abstraction, polymorphism, and inheritance. 

## Packages
Packages are the oldest and simplest way to group classes, such as `com.myapp.utils`. They don't enforce anything and are just a way to organize the structure

## Modules - Java 9+
> A Module is a group of closely related packages and resources along with a new module descriptor file.

Modules wrap packages and add the enforcement layer you're describing. A module declares in module-info.java which packages it exports (public API) and which it keeps internal. It also declares what it requires from other modules. The key thing that modules add is they are able to say X is an implementation detail and to encapsulate that package which the JVM will enforce.
## Applications

# References
- 