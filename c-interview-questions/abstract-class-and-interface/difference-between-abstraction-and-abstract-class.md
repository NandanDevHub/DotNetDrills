# Difference Between Abstraction and Abstract Class

| Aspect                      | Abstraction                                                                                         | Abstract Class                                                                                        |
| --------------------------- | --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **What is it?**             | A **concept** or **principle** in OOP that hides internal details and shows only essential features | A **concrete language feature** (a class) used to implement abstraction                               |
| **Purpose**                 | To reduce complexity by hiding unnecessary details and exposing only what’s needed                  | To provide a base class that cannot be instantiated, with partial implementation and abstract methods |
| **How is it achieved?**     | By using **abstract classes**, **interfaces**, or design patterns                                   | By declaring a class with the keyword `abstract` in C#                                                |
| **Example**                 | Showing only the **start()** method to users, hiding how the engine works                           | An `abstract class Vehicle` with some implemented methods and some abstract methods                   |
| **Can it be instantiated?** | N/A — it’s a concept, not a type                                                                    | No, abstract classes **cannot be instantiated** directly                                              |
| **In C# code?**             | Implemented through abstract classes and interfaces                                                 | Declared using `abstract class` with abstract or concrete methods                                     |

***

## Simple Explanation

* **Abstraction** is the **idea** of hiding complex details and showing only the necessary parts to the user.
* An **abstract class** is one way to **implement abstraction** in C# by defining some methods without implementation (abstract methods) and some with implementation.

***

## Quick Example

```csharp
// Abstraction concept: hiding details of how Start works
abstract class Vehicle
{
    public void Start()    // concrete method, visible to user
    {
        // hides complex engine start logic
        Console.WriteLine("Vehicle started.");
    }

    public abstract void Drive();  // abstract method, must be implemented by subclasses
}

class Car : Vehicle
{
    public override void Drive()
    {
        Console.WriteLine("Car is driving.");
    }
}
```

***

## Interview Tip

> When asked about **abstraction**, explain it as an **OOP principle** focused on hiding details. When asked about **abstract classes**, clarify it is a **C# feature to implement abstraction**, providing a mix of implemented and unimplemented methods.
