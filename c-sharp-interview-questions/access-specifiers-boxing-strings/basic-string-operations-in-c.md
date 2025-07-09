# Basic String Operations in C\#

#### 1. **Concatenation**

* Combining two or more strings.
* Can be done using:
  * The `+` operator
  * The `String.Concat()` method

**Example:**

```csharp
string s1 = "Hello";
string s2 = "World";

// Using +
string result1 = s1 + " " + s2;  // "Hello World"

// Using Concat
string result2 = String.Concat(s1, " ", s2);  // "Hello World"
```

***

#### 2. **Replace**

* Replaces occurrences of a specified substring with another substring.

**Example:**

```csharp
string text = "one one one";
string replaced = text.Replace("one", "two");  // "two two two"
```

***

#### 3. **Trim**

* Removes leading and trailing white spaces from a string.

**Example:**

```csharp
string spaced = "   hello   ";
string trimmed = spaced.Trim();  // "hello"
```

***

#### 4. **Contains**

* Checks if a string contains a specified substring.
* Returns `true` or `false`.

**Example:**

```csharp
string sentence = "This is a test";
bool hasTest = sentence.Contains("test");  // true
```

***

## Summary for Interview

> Basic string operations in C# include **concatenation** (using `+` or `Concat`), **Replace** (substitute parts of the string), **Trim** (remove spaces), and **Contains** (check substring existence). These are fundamental methods you use frequently to manipulate and query strings.
