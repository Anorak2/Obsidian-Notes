
2026-06-11

Tags: [[Software Engineering (SWE)]] [[Software Engineering (SWE)]]
# Design Patterns- Template
The Template Design Pattern is a behavioral design pattern that defines the overall structure (skeleton) of an algorithm in a base class. It allows subclasses to redefine or customize specific steps of the algorithm without changing its core structure. Importantly steps can also be either optional or mandatory, and the Abstract Class can also provide default implementations of methods.
![[Pasted image 20260611171635.png]]
- The abstract class defines the general template form, and some steps are implemented in the base class
- The concrete classes are then able to override the base implementation as they see fit

uses:
- a common base algorithm with some variations 
- reusing common code
- enforces structure/steps

Tea and coffee can both be made in generally the same four steps:
- boil water -> add main ingredient -> pour into cup -> add extras remain the same.
## Code Example


```java
/* Abstract class defining the template method */
abstract class BeverageMaker {
    // Template method defining the overall process
    void makeBeverage() {
        this.boilWater();
        this.brew();
        this.pourInCup();
        this.addCondiments();
    }

    // Abstract methods to be implemented by subclasses
    abstract void brew();
    abstract void addCondiments();

    // Common methods
    void boilWater() {
        System.out.println("Boiling water");
    }

    void pourInCup() {
        System.out.println("Pouring into cup");
    }
}
```
# References
- 