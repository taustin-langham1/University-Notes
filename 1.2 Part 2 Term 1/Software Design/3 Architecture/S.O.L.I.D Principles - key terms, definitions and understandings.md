
- coupling
- flow of control
- source code dependency

Overall wants from architecture (what makes good architecture) -> 
- **reduced** coupling
- **increased** cohesion

S SRP - a module responsible to only one actor
O OCP - closed for modification open for extension
L LSP - base class can sub for super class
I  ISP - forced to implement interfaces/not depend on methods they dont use 
D DIP - depend up on interfaces (abstractions) not concrete classes

ISP DIP
interface / segregation
dependency / inversion

interface
inversion
dependency
segregation


*Think of how reduced coupling and increased cohesion can be seen in each principle*

The solid principles are:

**Single Responsibility Principle (SRP)**

>"A module should be responsible to one, and only one, actor"
>OR
>" a class should have one and only one reason to change"
>// all have one responsibility (single responsibility)
>**Possibility of reuse increases!**

**Open-Closed Principle (OCP)**

> "Software entities should be **open for extension, but closed for modification**"
> 
> think of abstract class shape that a rectangle // any shape then implements to give its area

**Liskov Substitution Principle (LSP)**

>"subtypes must be substitutable for their base types"
>
>think about  if square, a subtype of rectangle, were

**Interface Segregation Principle (ISP)**

> The dependency of one class on another one should depend on the smallest possible interface
>  Clients should not be forced to implement interfaces they don't use (**no useless, dead weight, interfaces**)
>  Instead of one fat interface, many small interfaces are preferred based on groups of methods, each one serving one submodule (don't pet the tiger)

**Dependency Inversion Principle (DIP)**

>Depend upon abstractions (interfaces) not upon concrete classes

SDP - single dependency - a class must not have multiple actors dependent upon it
OCP - open closed - open for extension, closed for modification

LSP - Liskov Substitution - an actor must be able to use a base class in substitution for the superclass

ISL - interface segregation - not forced to use stuff

DIP - dependency inversion  - depend on interfaces not classes - they understand it as, do not rely on a specific instance of something, so like if person uses SQL, a better implementation would be i to have a database interface, with methods to save data, then have SQL types implement this interface

























