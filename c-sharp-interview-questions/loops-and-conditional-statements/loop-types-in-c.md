# Loop Types in C\#

#### 1. **While Loop**

* Repeats a block of code **while a condition is true**.
* Condition is checked **before** executing the loop body.
* Initialization done before the loop; increment/decrement inside the loop.

**Example:**

```csharp
int i = 0;
while (i < 5)
{
    Console.WriteLine(i);
    i++;
}
// Output: 0 1 2 3 4
```

***

#### 2. **Do-While Loop**

* Executes the loop body **at least once**, then checks the condition.
* Useful when you want the loop to run at least once regardless of condition.

**Example:**

```csharp
int j = 100;
do
{
    Console.WriteLine(j);
    j++;
} while (j < 10);
// Output: 100 (runs once even though condition false)
```

***

#### 3. **For Loop**

* Combines initialization, condition check, and increment/decrement in **one line**.
* Preferred for known iteration counts or when index is needed.

**Example:**

```csharp
for (int k = 0; k < 5; k++)
{
    Console.WriteLine(k);
}
// Output: 0 1 2 3 4
```

***

#### 4. **Foreach Loop**

* Designed to **iterate through collections or arrays** easily.
* No need to manually handle indexes or counts.
* Cleaner and safer for collection iteration.

**Example:**

```csharp
string[] fruits = { "Apple", "Banana", "Cherry" };
foreach (string fruit in fruits)
{
    Console.WriteLine(fruit);
}
// Output: Apple Banana Cherry
```

***

## When to Use Which Loop?

| Loop Type    | When to Use                                                                          |
| ------------ | ------------------------------------------------------------------------------------ |
| **while**    | When number of iterations is unknown and condition needs checking before loop starts |
| **do-while** | When loop must execute at least once regardless of condition                         |
| **for**      | When you know the number of iterations or need an index                              |
| **foreach**  | When iterating over collections or arrays without needing index                      |

***

#### Interview Tip:

> Understand not just syntax, but **practical use cases** and differences between loops. For example, `foreach` is safer and simpler for collections, while `for` provides index control.
