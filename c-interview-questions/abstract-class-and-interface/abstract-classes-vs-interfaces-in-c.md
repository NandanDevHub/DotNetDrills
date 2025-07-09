# Abstract Classes vs Interfaces in C\#

### What is an **Abstract Class**?

* An **abstract class** is a **class that cannot be instantiated directly**.
* It can contain:
  * **Implemented methods** (with body)
  * **Abstract methods** (without body) that derived classes must implement
  * Fields, properties, constructors
* Used when you want to share **common base behavior and state** among related classes, but also force derived classes to implement specific methods.

#### Example:

```csharp
abstract class Animal
{
    public void Eat()
    {
        Console.WriteLine("Eating food.");
    }

    public abstract void MakeSound();  // Must be implemented by derived classes
}

class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Bark!");
    }
}

class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow!");
    }
}
```

* You **cannot do** `new Animal()` but can create `new Dog()` or `new Cat()`.

***

### What is an **Interface**?

* An **interface** defines a **contract**: a set of methods, properties, or events that implementing classes must provide.
* It **cannot contain implementation** (until C# 8.0+ default interface methods, but mostly used as pure contracts).
* Supports **multiple inheritance**, since a class can implement multiple interfaces.
* Used to **define capabilities or behaviors** without dictating how they’re implemented.

#### Example:

```csharp
interface IFlyable
{
    void Fly();
}

interface ISwimmable
{
    void Swim();
}

class Bird : IFlyable
{
    public void Fly()
    {
        Console.WriteLine("Bird is flying.");
    }
}

class Fish : ISwimmable
{
    public void Swim()
    {
        Console.WriteLine("Fish is swimming.");
    }
}

class Duck : IFlyable, ISwimmable
{
    public void Fly()
    {
        Console.WriteLine("Duck is flying.");
    }
    
    public void Swim()
    {
        Console.WriteLine("Duck is swimming.");
    }
}
```

***

## Key Differences Between Abstract Classes and Interfaces

| Feature                    | Abstract Class                                                   | Interface                                                                           |
| -------------------------- | ---------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Can contain implementation | Yes (methods with body)                                          | Mostly no (until C# 8.0 default methods)                                            |
| Inheritance                | Single inheritance (a class can inherit only one abstract class) | Multiple inheritance (a class can implement multiple interfaces)                    |
| Fields                     | Can have fields                                                  | Cannot have fields                                                                  |
| Constructors               | Can have constructors                                            | Cannot have constructors                                                            |
| Access Modifiers           | Can have access modifiers (`public`, `protected`)                | Members are `public` by default, no modifiers allowed                               |
| When to use                | When you want to share code among closely related classes        | To define capabilities or behaviors to be implemented by any class                  |
| Versioning                 | Easier to add new methods without breaking derived classes       | Adding new members breaks existing implementations (unless default implementations) |

***

## Interview Notes

* Abstract classes let you **share code** among related classes.
* Interfaces provide **a contract for behavior**, supporting multiple inheritance.
* Use abstract classes when classes are **closely related**; use interfaces when you want **unrelated classes** to share behavior.
* You can implement **multiple interfaces** but inherit from only one abstract class.
* Abstract methods in abstract classes force derived classes to implement them.
* Interfaces require all members to be implemented (unless default interface methods are used).

***

## Sample Interview Answer

> “An **abstract class** allows you to define some default behavior and force derived classes to implement certain methods. It supports code reuse and can contain fields and constructors but supports only single inheritance. On the other hand, an **interface** defines a contract with no implementation (mostly), supports multiple inheritance, and is used to specify capabilities that unrelated classes can implement. Choosing between them depends on whether you need shared base behavior (abstract class) or just a contract for capabilities (interface).”

***

## Common Follow-up Questions

* Can a class implement multiple interfaces?
* Can an abstract class implement an interface?
* How do you decide when to use an abstract class vs an interface?
* What are default interface methods in C# 8.0+?
* Can interfaces have fields or constructors?

## When to Use **Interface** vs **Abstract Class** in Real Applications

***

### 1. **When to Use an Interface**

#### Scenario Example: Employees in a Company

* You have two classes: `PermanentEmployee` and `ContractualEmployee`.
* Both share some common **capabilities/requirements**:
  * They must have an **Email ID**.
  * They must have a **Manager**.
* You create an interface `IEmployee` that declares these properties or methods:

```csharp
interface IEmployee
{
    string Email { get; set; }
    string Manager { get; set; }
    void AssignEmail(string email);
    void AssignManager(string manager);
}
```

* Both `PermanentEmployee` and `ContractualEmployee` **implement this interface**:

```csharp
class PermanentEmployee : IEmployee
{
    public string Email { get; set; }
    public string Manager { get; set; }
    
    public void AssignEmail(string email) { Email = email; }
    public void AssignManager(string manager) { Manager = manager; }
}

class ContractualEmployee : IEmployee
{
    public string Email { get; set; }
    public string Manager { get; set; }
    
    public void AssignEmail(string email) { Email = email; }
    public void AssignManager(string manager) { Manager = manager; }
}
```

#### Why Interface Is Right Here?

* **It acts like a contract:** Any class implementing `IEmployee` **must** have these properties/methods.
* **Implementation details vary:** How `PermanentEmployee` or `ContractualEmployee` assigns or manages email/manager can be different.
* **Supports unrelated classes:** You may have other employee types that also implement `IEmployee`.
* **Interfaces provide maximum flexibility** — they only define _what_ must be done, not _how_.

***

### 2. **When to Use an Abstract Class**

#### Scenario Example: Employee Dress Code

* You have a base abstract class `EmployeeDressCode` that represents general dress code rules.
* You know some behavior is common to all employees, but some specifics depend on employee type or gender.

```csharp
abstract class EmployeeDressCode
{
    // Concrete method: same for all employees
    public void DressColor()
    {
        Console.WriteLine("Dress color is always blue.");
    }

    // Abstract method: implementation depends on derived classes
    public abstract void DressWear();  // e.g., male vs female dress differs
}

class MaleEmployeeDressCode : EmployeeDressCode
{
    public override void DressWear()
    {
        Console.WriteLine("Wear shirt and pants.");
    }
}

class FemaleEmployeeDressCode : EmployeeDressCode
{
    public override void DressWear()
    {
        Console.WriteLine("Wear saree or salwar.");
    }
}
```

#### Why Abstract Class Is Right Here?

* **You have common code** that applies to all employees (`DressColor()` method).
* **Some behavior is undefined yet** and must be implemented by derived classes (`DressWear()`).
* **You want to provide a base implementation with some shared functionality**.
* Abstract classes are useful when classes are **closely related** and share code/state.

***

### 3. **Summary: Interface vs Abstract Class**

| Aspect               | Interface                                                       | Abstract Class                                                        |
| -------------------- | --------------------------------------------------------------- | --------------------------------------------------------------------- |
| Purpose              | Define **contract** (methods/properties) with no implementation | Provide **base behavior + contract** with some method implementations |
| Implementation       | Classes **must implement** all interface members                | Classes **inherit** and may override or use base implementations      |
| Multiple inheritance | Supported (a class can implement many interfaces)               | Not supported (single inheritance only)                               |
| Use Case             | When you only know _what_ must be done, not _how_               | When you have some common behavior and some abstract behavior         |
| Flexibility          | Higher — implementation can change independently                | Moderate — base code may restrict flexibility                         |

***

### 4. **Additional Real-World Insights**

* In most projects, **interfaces are preferred** because they offer more flexibility to change implementation without breaking consumers.
* Abstract classes are handy when you want to **share code or state** between closely related classes.
* You can also **combine both**: use interfaces to define contracts and abstract classes to provide partial implementations.

***

## Interview Sample Answer

> "Use **interfaces** when you want to define a contract that multiple unrelated classes must follow, especially when you only know _what_ methods or properties should exist but not _how_ they will be implemented. For example, in a company, both permanent and contractual employees must have email and manager, but their implementation might differ, so an `IEmployee` interface fits well.
>
> On the other hand, use **abstract classes** when you have closely related classes that share common code or state, but also need to enforce certain methods to be implemented by subclasses. For example, for employee dress code, the dress color might always be blue (implemented in base class), but the specific dress wear differs for male and female employees, so an abstract class with a concrete method and abstract method is appropriate."
