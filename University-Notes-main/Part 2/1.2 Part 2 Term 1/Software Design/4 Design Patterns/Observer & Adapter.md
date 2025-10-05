

Design patterns are reusable solutions to common problems that occur in software development

Design patterns have 4 Elements

- the name
- the problem
- the solution
- the consequences

Three **categories** of Design Patterns

**Creational**
Techniques to create new objects -> Example: **Builder**

**Structural**
Techniques to compose larger structures of classes -> Example: **Adapter, Flyweight, Proxy**

**Behavioral**
concerned with the communication between objects -> Example: **Observer / Template Method**

**Builder *creational* pattern**

constructs complex objects by separating construction and representation

![[Pasted image 20250429194327.png]]




**Adapter *Structural* pattern**


**Client** collaborates with objects conforming to the **Target** interface. **Target** defines the domain-specific interface that Client uses. **Adapter** adapts the **Adaptee** to the **Target** interface. **Adaptee** defines an existing interface that needs adapting.
![[Pasted image 20250429191718.png]]


**Observer *behavioral* method**

define a subscription mechanism to notify multiple objects about interesting events that happen to the objects they are observing

![[Pasted image 20250429191200.png]]


**Proxy *Structural* pattern**

![[Pasted image 20250429194221.png]]


**Flyweight *structural* Design Pattern**

- aim to optimize memory usage by sharing a common state among multiple objects


![[Pasted image 20250429194442.png]]


**Elements of a Flyweight Design Pattern**

1. **Flyweight Interface/Class**

- Flyweight interface defines the interface for concrete flyweights. Typically, it includes a method to accept and process the extrinsic state

2. **Concrete Flyweight Classes**

- these are the actual flyweight objects that implement the flyweight interface.
- They store intrinsic states that can be shared among multiple objects

 3. **Flyweight Factory**

- Manages a pool of flyweight objects
- provides methods for clients to retrieve or create flyweight objects
- ensures flyweight objects are shared appropriately to maximize reusabiltiy

4. **Client**

- Uses flyweight objects to perform operations
- maintains or passes extrinsic state to flyweight objects when needed
- does not manage the lifecycle of flyweight objects but interacts with them via factory


How to implement:

**(1) Identify shared and unique data (2) Create flyweight class (3) Build Flyweight Factory (4) Pass Unique Data as Needed (5) Use Flyweights Instead of Creating New Objects**