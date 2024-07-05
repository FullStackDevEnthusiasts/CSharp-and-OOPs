### Set 2:

**6. What is the purpose of the `this` keyword in C#?**
- `this` is a reference to the current instance of the class.
- It is used to access members (fields, methods, properties) of the current object.
- `this` can be used to distinguish between instance variables and parameters if they have the same name.
- Example: `public void SetName(string name) { this.name = name; }`
- It can also be used to call another constructor from within a constructor.
- Example: `public Car() : this("Default Model") { }`

**7. Explain the concept of properties in C#.**
- Properties provide a way to access and modify the fields of a class.
- They use `get` and `set` accessors to encapsulate the logic for retrieving and assigning values.
- Properties can have different access levels for `get` and `set`.
- Example: `public string Name { get; set; }`
- Automatic properties can be used for simple properties without additional logic.
- Example: `public int Age { get; private set; }`
- Backing fields can be used with properties to add validation logic or other operations.

**8. What is the significance of the `static` keyword in C#?**
- `static` keyword denotes that a member belongs to the type itself rather than to a specific object.
- Static members are shared among all instances of a class.
- Static methods and properties can be accessed without creating an instance of the class.
- Example: `public static int InstanceCount { get; set; }`
- Static constructors initialize static members and are called automatically before any static members are accessed.
- Example: `static Car() { InstanceCount = 0; }`

**9. What is the difference between value types and reference types in C#?**
- Value types store the actual data, while reference types store a reference to the data.
- Value types are stored in the stack, whereas reference types are stored in the heap.
- Examples of value types: `int`, `float`, `bool`, `struct`
- Examples of reference types: `class`, `string`, `array`, `interface`
- Value types have a default value (e.g., 0 for integers), while reference types have a default value of `null`.
- Value types cannot be `null` unless they are nullable (`int?`), but reference types can be `null`.

**10. How does exception handling work in C#?**
- Exception handling is done using `try`, `catch`, `finally`, and `throw` keywords.
- `try` block contains the code that may throw an exception.
- `catch` block catches and handles the exception.
- `finally` block contains code that runs regardless of whether an exception was thrown.
- `throw` keyword is used to explicitly throw an exception.
- Example: 
  ```csharp
  try {
      int result = 10 / 0;
  } catch (DivideByZeroException ex) {
      Console.WriteLine("Cannot divide by zero.");
  } finally {
      Console.WriteLine("Cleanup code.");
  }
  ```
