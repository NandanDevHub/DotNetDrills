# Can You Create an Instance of an Abstract Class or Interface?

> **No, you cannot create an instance of an abstract class or an interface.**
>
> Both **abstract classes** and **interfaces** are designed to serve as <mark style="background-color:orange;">**base types**</mark>—they define a contract or a partial implementation for other classes to inherit or implement.
>
> Because they are incomplete by design, the compiler will **throw an error** if you try to instantiate them directly.
>
> For example:
>
> ```csharp
> IEmployee emp = new IEmployee();         // Compile-time error
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

#### How to use them?

```csharp
abstract class Employee
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
