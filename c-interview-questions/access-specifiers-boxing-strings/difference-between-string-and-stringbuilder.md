# Difference Between string and StringBuilder

#### 1. **String is Immutable**

* Once a string is created, **its value cannot be changed**.
* Any operation that seems to modify the string actually **creates a new string object** in memory.
* Example:

```csharp
string str1 = "Hello";
str1 = str1 + " World";  // Creates a new string object, str1 points to new string now
```

* This means repeated modifications cause **multiple new strings to be created**, which can hurt performance.

***

#### 2. **StringBuilder is Mutable**

* `StringBuilder` allows you to **modify the string value without creating new objects**.
* It **updates the existing buffer in memory**, which is efficient for multiple or large modifications.
* Example:

```csharp
StringBuilder sb = new StringBuilder("Hello");
sb.Append(" World");  // Modifies the same object, no new string created
```

***

#### 3. **When to Use What?**

| Scenario                       | Use `string`                       | Use `StringBuilder`                         |
| ------------------------------ | ---------------------------------- | ------------------------------------------- |
| Few or simple string changes   | `string`                           | Not necessary                               |
| Many concatenations/updates    | Avoid `string` due to immutability | Use `StringBuilder` for better performance  |
| Performance-critical scenarios | `string` can cause overhead        | `StringBuilder` avoids repeated allocations |

***

## When to Use `string` and When to Use `StringBuilder` in Real Applications

***

#### Use **`string`** when:

* You **change or concatenate the string only once or twice**.
* Your string operations are **simple and infrequent**.
* Because `string` is **lightweight and easy to use**.
* Example: Forming a message or simple output.

```csharp
string greeting = "Hello";
greeting += " World";  // Fine for few concatenations
```

***

#### Use **`StringBuilder`** when:

* You have to **change or build a string multiple times** (especially in loops).
* Performance matters — **avoiding creation of multiple string objects** saves memory and CPU.
* Example: Constructing large dynamic text, building complex strings iteratively.

```csharp
StringBuilder sb = new StringBuilder("Hello");
for(int i=0; i<100; i++)
{
    sb.Append(" World");
}
string result = sb.ToString();
```

* Only **one string object is updated in memory**, no new strings created on each change.

***

#### Why?

| Feature          | `string`                                 | `StringBuilder`                      |
| ---------------- | ---------------------------------------- | ------------------------------------ |
| **Mutability**   | Immutable (creates new object on change) | Mutable (modifies existing object)   |
| **Performance**  | Slow for many changes                    | Fast for multiple changes            |
| **Memory Usage** | More when changed repeatedly             | Efficient memory usage               |
| **Use Case**     | Few/simple concatenations                | Heavy, repeated string manipulations |

#### Summary for Interview:

> * `string` in C# is **immutable**, meaning changes create new string instances.
> * `StringBuilder` is **mutable**, so it modifies the existing object without creating new ones.
> * Use `string` for simple, infrequent modifications and `StringBuilder` when performing many modifications to improve performance.
> * If your string changes only once or twice, use `string` because it is lightweight and simple.\
>   If you expect many modifications or concatenations (like in loops), use `StringBuilder` for better performance and memory efficiency.
