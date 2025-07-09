# Access Specifiers in C\#

| Specifier              | Where Accessible?                                                       | Description                                                  |
| ---------------------- | ----------------------------------------------------------------------- | ------------------------------------------------------------ |
| **public**             | Anywhere (any assembly or project)                                      | Accessible from any other code — no restrictions             |
| **private**            | Only within the same class                                              | Accessible only inside the class where declared              |
| **protected**          | Within the same class and derived classes (even in other assemblies)    | Accessible in the class and its subclasses                   |
| **internal**           | Within the same assembly/project only                                   | Accessible only inside the same assembly (project)           |
| **protected internal** | Within the same assembly **OR** in derived classes outside the assembly | Accessible inside assembly or by subclasses outside assembly |

***

#### Quick Explanation:

* **public**: No restriction, accessible everywhere.
* **private**: Most restrictive, only inside the declaring class.
* **protected**: Accessible in the class itself and any class that inherits from it.
* **internal**: Accessible anywhere within the same compiled assembly (like the same project).
* **protected internal**: Accessible either **within the assembly** or **in subclasses** outside the assembly.

***

#### Visual Example

```csharp
public class BaseClass
{
    public int PublicVar;              // Accessible anywhere
    private int PrivateVar;            // Only inside BaseClass
    protected int ProtectedVar;        // BaseClass and derived classes
    internal int InternalVar;          // Same assembly only
    protected internal int ProtInternalVar;  // Same assembly or derived classes anywhere
}
```

***

<mark style="color:orange;">Internal : Default Access Modifier in the class</mark>

#### Interview Tip

> When asked about access modifiers, always mention **where the members can be accessed from** and give **examples of use cases** for each.
