# Interfaces Can You?

## 🔹 Can Interfaces Have Method Bodies?

#### Traditional Interfaces (Before C# 8.0)

* Interfaces only **declare** methods, properties, or events with **no implementation** (no method bodies).
* All implementing classes must provide their own implementation.
* Example:

```csharp
csharpCopyinterface IEmployee
{
    void Role();  // Declaration only, no body allowed
}
```

***

#### What Changed in C# 8.0?

* From **C# 8.0 onwards**, **default interface methods** are allowed.
* You **can provide a method body** inside an interface.
* This enables **concrete method implementations in interfaces**.

Example:

```csharp
csharpCopyinterface IEmployee
{
    void Role()  // Method with a body inside interface
    {
        Console.WriteLine("Default role implementation.");
    }
}
```

***

#### Why Did Microsoft Add This Feature?

*   **Backward compatibility and evolution of APIs**:

    Imagine a project where `IEmployee` interface was created initially with only method declarations (no bodies).
* After a year, you want to **add a concrete method implementation** (for example, a default `Role()` method).
* If you convert the interface to an abstract class, it would require **massive code changes** because classes might already inherit from other classes (single inheritance limitation).
* Default interface methods allow **adding new functionality to interfaces without breaking existing implementations**.

***

#### When Should You Define Methods in Interfaces?

| Scenario                                                                               | Recommendation                                       |
| -------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| Starting a **new project**                                                             | Use **abstract classes** if method bodies are needed |
| Evolving an **existing interface** (adding new methods without breaking existing code) | Use **default interface methods** in C# 8.0+         |
| When you want to provide **optional or default behavior**                              | Use default interface methods                        |

***

#### Interview Notes: Best Practices

* Use default interface methods **carefully**; they can make the design more complex.
* Prefer abstract classes for **shared base implementations** when starting fresh.
* Default interface methods are mainly for **API evolution and backward compatibility**.
* Remember, not all .NET runtimes or older C# versions support this feature.

***

#### Sample Interview Answer

> “Yes, starting with C# 8.0, interfaces can have method bodies called default interface methods. This feature was introduced to allow API designers to add new functionality to interfaces without breaking existing implementations. For example, if an interface originally had only method declarations, and later we want to provide a default implementation, default interface methods allow us to do that. However, when starting a new project, if you need method bodies, it’s generally better to use abstract classes for clearer design and maintainability.”

## 🔹 Can You Create an Instance of an Abstract Class or Interface?

#### Interview-Ready Answer:

> **No, you cannot create an instance of an abstract class or an interface.**
>
> Both **abstract classes** and **interfaces** are designed to serve as <mark style="background-color:orange;">**base types**</mark>—they define a contract or a partial implementation for other classes to inherit or implement.
>
> Because they are incomplete by design, the compiler will **throw an error** if you try to instantiate them directly.
>
> For example:
>
> ```csharp
> csharpCopyIEmployee emp = new IEmployee();         // Compile-time error
> Employee emp = new Employee();           // If Employee is abstract, compile-time error
> ```
>
> You must create an instance of a **concrete class** that derives from the abstract class or implements the interface.

***

#### Why?

* **Abstract classes** may have abstract methods without implementation, so they can't be fully instantiated.
* **Interfaces** only declare method signatures with no implementation (traditionally), so they can't create usable objects.
* Their role is to **provide structure and enforce contracts** for derived classes.

***

#### Bonus: How to use them?

```csharp
csharpCopy abstract class Employee
{
    public abstract void Work();
}

interface IEmployee
{
    void Work();
}

class PermanentEmployee : Employee, IEmployee
{
    public override void Work()
    {
        Console.WriteLine("Working permanently");
    }
}

class Program
{
    static void Main()
    {
        // Cannot create instance of Employee or IEmployee directly
        // Employee e = new Employee();    // Error
        // IEmployee i = new IEmployee();  // Error

        PermanentEmployee pe = new PermanentEmployee(); // OK
        pe.Work();
    }
}
```

***

#### Summary for Interview

* Both **abstract classes** and **interfaces** cannot be instantiated.
* They exist to **be inherited or implemented** by concrete classes.
* Trying to instantiate them directly results in **compile-time errors**.
