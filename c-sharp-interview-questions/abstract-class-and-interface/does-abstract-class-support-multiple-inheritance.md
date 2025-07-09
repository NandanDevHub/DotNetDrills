# Does Abstract Class Support Multiple Inheritance?

> **No, C# does not support multiple inheritance with classes, including abstract classes.**

***

#### Explanation:

* A class (including an abstract class) can **inherit from only one base class** (abstract or concrete).
* Trying to inherit from **two abstract classes at the same time causes a compile-time error**.

Example causing error:

```csharp
abstract class A { }
abstract class B { }

class C : A, B  // Compile-time error: cannot inherit from multiple classes
{
}
```

***

#### How to Achieve Multiple Inheritance Behavior?

* C# allows a class to **implement multiple interfaces**.
* Interfaces provide a way to achieve **multiple inheritance of behavior** without inheriting implementation.

Example:

```csharp
csharpCopyinterface IA { void MethodA(); }
interface IB { void MethodB(); }

class C : IA, IB
{
    public void MethodA() { }
    public void MethodB() { }
}
```

***

#### Summary for Interview:

* C# supports **single inheritance for classes** (including abstract classes).
* **Multiple interfaces** can be implemented by a class to achieve multiple inheritance-like behavior.
* This design avoids the complexity and ambiguity that multiple inheritance can cause.
