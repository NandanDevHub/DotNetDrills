# Can Interfaces Have Method Bodies?

#### Traditional Interfaces (Before C# 8.0)

* Interfaces only **declare** methods, properties, or events with **no implementation** (no method bodies).
* All implementing classes must provide their own implementation.
* Example:

```csharp
interface IEmployee
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
interface IEmployee
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

