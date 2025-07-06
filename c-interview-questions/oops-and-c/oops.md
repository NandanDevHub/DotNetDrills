---
layout:
  width: default
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# OOPS

## 🔹 What is Object-Oriented Programming (OOP)?

#### Interview-Ready Explanation:

> **Object-Oriented Programming (OOP)** is a programming paradigm where the design and structure of software revolve around **objects** — entities that combine **data** and **behavior**.
>
> Instead of writing procedures or functions to perform operations, you create **objects** that represent real-world things or concepts and interact with one another.
>
> This approach models complex systems in a way that is easier to design, understand, and maintain.

***

## 🔹 Core Concepts of OOP

| Concept           | Description                                                                                                                                            | Interview Notes / Examples                                                |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------- |
| **Class**         | Blueprint or template for creating objects. Defines properties (data) and methods (behavior).                                                          | `class Car { public string Model; public void Drive() { ... } }`          |
| **Object**        | An instance of a class. Represents a specific entity created from the class blueprint.                                                                 | `Car myCar = new Car();`                                                  |
| **Encapsulation** | Bundling data and methods together and restricting direct access to some of the object’s components (using access modifiers like `private`, `public`). | Protects data integrity; e.g., private fields with public getters/setters |
| **Inheritance**   | Mechanism by which one class acquires properties and behaviors of another class.                                                                       | Enables code reuse; e.g., `class SportsCar : Car { ... }`                 |
| **Polymorphism**  | Ability of objects to take many forms. Methods can behave differently based on the object that calls them (method overriding and overloading).         | Runtime polymorphism via virtual/override methods in C#                   |
| **Abstraction**   | Hiding internal implementation details and exposing only the necessary features.                                                                       | Interfaces and abstract classes; user works with _what_ not _how_         |

***

## 🔹 How OOP Solves Problems

* OOP maps real-world entities to software objects.
* Improves **code organization**, **reusability**, and **maintainability**.
* Facilitates **modular programming**: components can be updated independently.
* Supports **team collaboration** by defining clear interfaces and contracts.

***

## 🔹 Simple C# Example Illustrating OOP

```csharp
csharpCopy// Class: blueprint for Car
class Car
{
    // Encapsulated field
    private string model;

    // Property (Encapsulation)
    public string Model
    {
        get { return model; }
        set { model = value; }
    }

    // Method: behavior
    public void Drive()
    {
        Console.WriteLine($"{Model} is driving.");
    }
}

// Inheritance: SportsCar inherits from Car
class SportsCar : Car
{
    public void TurboBoost()
    {
        Console.WriteLine($"{Model} is boosting with turbo!");
    }
}

class Program
{
    static void Main()
    {
        SportsCar myCar = new SportsCar();
        myCar.Model = "Ferrari";
        myCar.Drive();        // Polymorphism: uses base class method
        myCar.TurboBoost();   // SportsCar-specific method
    }
}
```

***

## 🔹 Interviewer Tips: What Interviewers Look For

* Can you **explain each OOP concept** clearly with examples?
* Do you understand the difference between **class and object**?
* Can you discuss how **encapsulation** improves security?
* Can you describe **inheritance** and its pros and cons?
* Can you explain **polymorphism** and give real-world examples?
* Do you know the difference between **abstract classes and interfaces**?
* Can you relate OOP concepts to C# syntax and features?

***

## 🔹 Common Follow-up Questions

* What is the difference between **method overloading** and **method overriding**?
* How does C# implement **polymorphism**?
* What is an **interface**, and how is it different from an abstract class?
* How can you enforce encapsulation in C#?
* What are some advantages and disadvantages of using inheritance?
* How do you implement **abstraction** in C#?
