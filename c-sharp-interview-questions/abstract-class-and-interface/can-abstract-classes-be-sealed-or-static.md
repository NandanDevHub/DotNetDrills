# Can Abstract Classes Be Sealed or Static?

#### 1. **Can Abstract Classes Be Sealed?**

* **No, abstract classes cannot be sealed.**
* **Why?**
  * Abstract classes are meant to be **inherited** so you can extend their behavior.
  * Sealed classes **cannot be inherited**.
* Therefore, a class **cannot be both abstract and sealed** because these two are contradictory.

```csharp
// This will cause a compile-time error
abstract sealed class MyClass
{
}
```

***

#### 2. **Can Abstract Classes Be Static?**

* **No, abstract classes cannot be static.**
* **Why?**
  * Abstract classes are meant to be **base classes for inheritance**.
  * Static classes **cannot be instantiated or inherited** and only contain static members.
* So, making a class both abstract and static is **not allowed**.

```csharp
// This will cause a compile-time error
abstract static class MyClass
{
}
```

***

#### Quick summary for interviews:

| Modifier   | Allowed on Abstract Classes? | Reason                                                                        |
| ---------- | ---------------------------- | ----------------------------------------------------------------------------- |
| **Sealed** | No                           | Abstract means inheritable, sealed means no inheritance — contradictory       |
| **Static** | No                           | Abstract requires inheritance, static disallows inheritance and instantiation |
