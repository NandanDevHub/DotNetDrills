# Boxing and Unboxing

## Value Types vs Reference Types

| Aspect        | Value Types                      | Reference Types                                |
| ------------- | -------------------------------- | ---------------------------------------------- |
| Storage       | Stored directly in the **stack** | Stored in the **heap**, reference on the stack |
| Examples      | `int`, `float`, `bool`, `struct` | `class`, `string`, arrays, delegates           |
| Copy behavior | Copies the actual data           | Copies the reference (pointer) to the data     |
| Lifetime      | Lifetime tied to scope/block     | Lifetime managed by Garbage Collector (GC)     |

***

## What is Boxing?

* **Boxing** is the process of **converting a value type to a reference type** by wrapping the value inside an object on the heap.
* Happens automatically when a value type needs to be treated like an object (e.g., storing `int` in a variable of type `object`).

#### Example:

```csharp
int x = 10;            // value type
object obj = x;        // boxing happens here — int is wrapped into an object
```

***

## What is Unboxing?

* **Unboxing** is the reverse process — extracting the value type from the boxed object.
* You must explicitly cast the object back to the original value type.

#### Example:

```csharp
object obj = 10;        // boxed int
int y = (int)obj;       // unboxing — extract int from object
```

***

## Why Boxing and Unboxing?

* Allows **value types to be treated as objects** so they can be used in contexts that require reference types (like collections before generics).
* Enables **polymorphism and code reuse** because everything derives from `object`.

***

## Performance Note

* Boxing and unboxing **have performance costs**:
  * Boxing allocates memory on the heap.
  * Unboxing requires type checking and casting.
* Excessive boxing/unboxing should be avoided for performance-critical code.

***

## Interview Summary

> **Boxing** converts a value type to a reference type by wrapping it in an object.\
> **Unboxing** extracts the value type back from the object.\
> **Value types** store data directly, live on the stack, and copy data when assigned.\
> **Reference types** store references to data on the heap, and assignments copy references.\
> Boxing/unboxing are used when value types need to be treated as objects, but they incur performance overhead.

## Which One is Explicit? Boxing or Unboxing?

#### Answer:

* **Boxing is implicit** — it happens automatically without any special syntax.
* **Unboxing is explicit** — you must explicitly cast the object back to the original value type.

***

#### Why?

* When you assign a value type to an `object` (boxing), the compiler automatically wraps it — no cast needed.

```csharp
int x = 10;
object obj = x;   // Boxing — implicit, no cast required
```

* When you extract the value type from the object (unboxing), you **must provide the type explicitly** via casting.

```csharp
object obj = 10;
int y = (int)obj; // Unboxing — explicit cast required
```

***

#### Interview Tip

> Always remember: **Boxing is implicit**, but **unboxing requires an explicit cast** to tell the compiler what exact value type to extract
