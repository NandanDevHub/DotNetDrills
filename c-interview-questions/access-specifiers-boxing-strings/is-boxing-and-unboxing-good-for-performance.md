# Is Boxing and Unboxing Good for Performance?

> **No, boxing and unboxing have a negative impact on performance.**

***

#### Why?

* **Boxing** involves creating a new object on the heap to wrap the value type. This means:
  * Memory allocation happens, which is slower than stack allocation.
  * Garbage collector (GC) has to clean up these objects later, adding overhead.
* **Unboxing** involves:
  * Checking the type of the object at runtime.
  * Extracting the value type, which requires explicit casting and additional CPU instructions.

***

#### When to Avoid Boxing/Unboxing?

* In **performance-critical code** or **high-frequency operations**, frequent boxing/unboxing can cause:
  * Increased memory usage.
  * More GC pressure.
  * Slower execution.

***

#### How to Avoid Boxing?

* Use **generics** (`List<int>`, `Dictionary<string, int>`) instead of collections like `ArrayList` which store objects.
* Use **value type methods directly** without converting to `object`.

***

#### Interview Summary

> Boxing and unboxing add overhead because they involve memory allocation and runtime type checks. They should be avoided in performance-sensitive areas by using generics and minimizing conversions between value and reference types.
