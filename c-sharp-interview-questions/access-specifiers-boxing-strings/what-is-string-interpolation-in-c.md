# What is String Interpolation in C#?

#### Definition:

> **String Interpolation** is a technique that lets you insert variable values or expressions directly into string literals, making the code easier to read and write.

***

#### Traditional Concatenation:

```csharp
string name = "Alice";
string message = "Hello " + name + ", welcome!";

Console.WriteLine(message);  // Output: Hello Alice, welcome!
```

* Uses `+` operator to combine strings and variables.

***

#### String Interpolation (introduced in C# 6.0):

* Use the `$` symbol before the string.
* Insert variables or expressions inside `{}` within the string.

```csharp
string name = "Alice";
string message = $"Hello {name}, welcome!";

Console.WriteLine(message);  // Output: Hello Alice, welcome!
```

***

#### Benefits of String Interpolation:

* **Cleaner and easier to read code**, especially with multiple variables.
* Avoids complex concatenation with many `+` operators.
* Supports expressions inside the `{}`, e.g., `{$"{name.ToUpper()}"}`.
* Improves maintainability.

***

#### Interview Summary:

> String interpolation in C# uses the `$` prefix and `{}` placeholders to embed variables or expressions inside strings. It’s more concise and readable compared to traditional concatenation, especially when dealing with multiple variables.
