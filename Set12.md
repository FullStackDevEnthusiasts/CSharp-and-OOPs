### Set 12:

**56. What is the `using` statement in C# and how is it used?**
- The `using` statement is used to ensure that `IDisposable` objects are properly disposed of when they are no longer needed.
- It provides a convenient syntax for managing resources, such as file handles, database connections, and streams.
- Example:
  ```csharp
  using (var stream = new FileStream("example.txt", FileMode.Open)) {
      // Use the stream
  } // Stream is automatically disposed of here
  ```
- The `using` statement automatically calls the `Dispose` method on the object at the end of the block.
- It can be used with multiple objects by separating them with commas.
- The `using` statement improves code readability and helps prevent resource leaks by ensuring deterministic disposal.

**57. What is pattern matching in C# and how is it used?**
- Pattern matching provides a way to check a value against a pattern and, if the match succeeds, extract values from the object.
- It is used with `is` expressions, switch statements, and switch expressions.
- Example with `is` expressions:
  ```csharp
  if (obj is string s) {
      Console.WriteLine($"String length: {s.Length}");
  }
  ```
- Example with switch expressions:
  ```csharp
  object obj = "Hello";
  var result = obj switch {
      string s => $"String: {s}",
      int i => $"Integer: {i}",
      _ => "Unknown type"
  };
  Console.WriteLine(result);
  ```
- Pattern matching enhances readability and reduces the need for explicit type checks and casts.
- It supports various patterns, including type patterns, property patterns, and positional patterns, making it a versatile feature for working with complex data structures.

**58. What is the purpose of the `readonly` keyword in C# and how is it used?**
- The `readonly` keyword is used to declare fields that can only be assigned during initialization or in the constructor of the class.
- It ensures that the field cannot be modified after the object is constructed, providing immutability.
- Example:
  ```csharp
  public class Example {
      public readonly int Value;
      
      public Example(int value) {
          Value = value;
      }
  }
  ```
- `readonly` fields can be initialized at the point of declaration or in the constructor.
- They provide a way to create immutable objects, improving code reliability and preventing accidental modifications.
- `readonly` fields are particularly useful for constants that are determined at runtime and need to remain unchanged throughout the object's lifetime.

**59. What are local functions in C# and how are they used?**
- Local functions are functions defined within the scope of another function.
- They provide a way to encapsulate helper methods that are only relevant within a specific context.
- Example:
  ```csharp
  public void ProcessData() {
      int Compute(int a, int b) {
          return a + b;
      }
      
      int result = Compute(2, 3);
      Console.WriteLine(result);
  }
  ```
- Local functions can access variables from the enclosing method, enabling them to work closely with the outer method's logic.
- They improve code readability by keeping related logic together and reducing the need for private helper methods.
- Local functions support all the features of regular methods, including recursion, generics, and async/await.

**60. What is a nullable value type in C# and how is it used?**
- Nullable value types allow value types (such as `int`, `double`, `bool`) to represent a value or a null state.
- They are declared using the `?` syntax, indicating that the type can hold a null value.
- Example:
  ```csharp
  int? nullableInt = null;
  if (nullableInt.HasValue) {
      Console.WriteLine(nullableInt.Value);
  } else {
      Console.WriteLine("Value is null");
  }
  ```
- Nullable value types are commonly used for database fields, optional parameters, and scenarios where a value may be undefined or absent.
- The `Nullable<T>` struct provides methods and properties to work with nullable types, such as `HasValue` and `Value`.
- Nullable value types enhance flexibility and compatibility with data sources that may contain null values.
