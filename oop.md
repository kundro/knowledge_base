# Object-Oriented Programming (OOP)

## OOP Principal Advantages:
- Reusability, security, and design benefits.
- Compared to functional programming, OOP allows a program to work with instances of multiple function groups simultaneously, whereas functional programming cannot handle multiple instances of a single function group.

## Core OOP Concepts

### 1. Encapsulation
- Objects restrict the visibility of their attributes and methods.
- The implementation of an object is encapsulated *(hidden from the outside)*.

### 2. Polymorphism
- Identical methods behave differently in different classes.
- **Interface** - Defines methods without implementation. Method names are the same, but the implementation is specific to each class.

### 3. Inheritance
- Ability to use an existing class to derive a new one.
- Derived classes inherit the data and methods of the superclass.
- We can override existing logic or add new methods.

### 4. Abstraction
- **Abstract class** - Cannot be instantiated. Defines common behavior and enforces child classes to implement abstract methods.

### Access Modifiers
- **PUBLIC** - Accessible everywhere.
- **PROTECTED** - Access only within the class and subclasses.
- **PRIVATE** - Access only within the class.

## Advanced OOP Concepts for SAP CAP/BTP

### Composition vs. Inheritance
- **Composition** is often preferred over inheritance as it promotes flexibility.
- Example: In SAP CAP, services are composed of entities rather than relying solely on inheritance.

### SOLID Principles
- **Single Responsibility Principle (SRP):** A class should have only one reason to change.
- **Open/Closed Principle (OCP):** Software entities should be open for extension but closed for modification.
- **Liskov Substitution Principle (LSP):** Subtypes should be replaceable by their base types.
- **Interface Segregation Principle (ISP):** Clients should not be forced to depend on methods they do not use.
- **Dependency Inversion Principle (DIP):** High-level modules should depend on abstractions rather than low-level modules.

### Dependency Injection
- Used extensively in SAP CAP and SAP BTP services.
- Helps manage dependencies and improves testability.

### Design Patterns
- **Factory Pattern:** Used to create objects without specifying the exact class.
- **Singleton Pattern:** Ensures a class has only one instance (useful for service layers in CAP).
- **Repository Pattern:** Helps abstract database interactions (e.g., CAP’s `@cds.persistence`).

### Event-Driven Architecture in CAP
- CAP services interact using events (`on`, `before`, `after` handlers).
- Example:
  ```js
  this.on('CREATE', 'Orders', async (req) => {
      // Custom logic
  });
  ```

### OOP in CAP & Node.js
- CAP is primarily declarative but allows custom logic via JavaScript (Node.js).
- Understanding JavaScript OOP (prototypes, classes, `this` context) is useful.
