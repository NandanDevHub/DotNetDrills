# Do Abstract Classes Have Constructors in C#?

#### Common thought:

> Since **abstract classes cannot be instantiated** (you can’t create objects of abstract classes directly), you might think **they don’t have constructors**.

#### But the reality is:

> **Yes, abstract classes can have constructors!**

***

#### Why?

* **Abstract classes are meant to be inherited**, and constructors in the abstract class are called **when a derived class object is created**.
* The base class constructor runs **first**, initializing base class parts, then the derived class constructor runs.
* This helps set up common data or perform setup logic needed for all derived classes.

***

#### Simple Example:

```csharp
abstract class Employee
{
    public Employee()
    {
        Console.WriteLine("Abstract class constructor called.");
    }
}

class PermanentEmployee : Employee
{
    public PermanentEmployee()
    {
        Console.WriteLine("Derived class constructor called.");
    }
}

class Program
{
    static void Main()
    {
        PermanentEmployee emp = new PermanentEmployee();

        // Output:
        // Abstract class constructor called.
        // Derived class constructor called.
    }
}
```

* When you create a `PermanentEmployee` object:
  * First, the `Employee` (abstract class) constructor runs.
  * Then, the `PermanentEmployee` constructor runs.

***

#### Interview Summary:

> Abstract classes **can have constructors** even though you cannot instantiate them directly. These constructors are called when a derived class object is created to initialize the base part of the object.
