# Difference Between continue and break in Loops

#### 1. **Continue Statement**

* When the loop encounters a `continue` statement, it **skips the remaining code in the current iteration**.
* It immediately jumps to the **start of the next iteration** of the loop.
* Useful when you want to **skip certain values but continue looping**.

**Example:**

```csharp
for (int i = 0; i < 5; i++)
{
    if (i == 3)
        continue;  // Skip the rest of the loop body when i == 3

    Console.WriteLine(i);
}
// Output: 0 1 2 4
```

* When `i` is 3, the loop skips printing `3` and continues with the next iteration.

***

#### 2. **Break Statement**

* When the loop encounters a `break` statement, it **immediately exits the entire loop**.
* No further iterations occur after `break`.
* Useful when you want to **stop looping based on a condition**.

**Example:**

```csharp
for (int i = 0; i < 5; i++)
{
    if (i == 3)
        break;  // Exit the loop when i == 3

    Console.WriteLine(i);
}
// Output: 0 1 2
```

* When `i` is 3, the loop stops entirely and exits.

***

#### Summary:

| Statement    | Behavior                                   | Use Case                             |
| ------------ | ------------------------------------------ | ------------------------------------ |
| **continue** | Skip current iteration and proceed to next | Skip specific values in the loop     |
| **break**    | Exit loop immediately                      | Stop looping when a condition is met |

***

#### Interview Tip:

> Remember, `continue` moves control to the next iteration, skipping remaining code in the loop body, while `break` stops the loop entirely and exits.
