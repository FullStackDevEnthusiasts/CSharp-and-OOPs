
### Set 10:

**46. Explain the purpose and use of `unsafe` code in C#.**
- `unsafe` code allows the use of pointer types and direct memory manipulation.
- It is used in scenarios where performance is critical or interoperability with low-level APIs is required.
- Example:
  ```csharp
  unsafe {
      int* ptr = &myInt;
      *ptr = 10;
  }
  ```
- `unsafe` code must be compiled with the `/unsafe` switch and marked with the `unsafe` keyword.
- It enables pointer arithmetic, type casting, and other low-level operations.
- Using `unsafe` code bypasses some of the safety mechanisms of the .NET runtime, so it should be used with caution.

**47. What are tuples in C# and how are they used?**
- Tuples are data structures that can store a fixed-size sequence of elements of different types.
- They provide a lightweight way to return multiple values from a method.
- Example:
  ```csharp
  (int, string) GetPersonInfo() {
      return (1, "John Doe");
  }
  
  var person = GetPersonInfo();
  Console.WriteLine($"ID: {person.Item1}, Name: {person.Item2}");
  ```
- C# 7.0 introduced tuple literals and named elements:
  ```csharp
  (int id, string name) GetPersonInfo() {
      return (1, "John Doe");
  }
  
  var person = GetPersonInfo();
  Console.WriteLine($"ID: {person.id}, Name: {person.name}");
  ```
- Tuples improve code readability and convenience for grouping related data without creating a separate class.
- They are commonly used in methods that need to return multiple values.

**48. What is a `sealed` class in C# and when would you use it?**
- A `sealed` class cannot be inherited by any other class.
- It is used to prevent further derivation, ensuring the class behavior remains unchanged.
- Example:
  ```csharp
  public sealed class MyClass {
      public void Display() {
          Console.WriteLine("Hello, Sealed Class!");
      }
  }
  ```
- `sealed` classes can improve performance by enabling certain optimizations by the compiler and runtime.
- They are used when a class is fully implemented and should not be extended, such as utility classes or specific application logic.
- Sealing a class can also be a design decision to enforce encapsulation and prevent unintended modifications.

**49. What are lambda expressions in C# and how are they used?**
- Lambda expressions are a concise way to represent anonymous methods.
- They are used for writing inline expressions for delegates, LINQ queries, and event handling.
- Example:
  ```csharp
  Func<int, int, int> add = (a, b) => a + b;
  Console.WriteLine(add(2, 3)); // Output: 5
  ```
- Lambda expressions have the syntax `(parameters) => expression`.
- They can have multiple statements enclosed in `{}` and can capture variables from the enclosing scope.
- Example of a LINQ query using lambda expressions:
  ```csharp
  List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
  var evenNumbers = numbers.Where(n => n % 2 == 0).ToList();
  foreach (var num in evenNumbers) {
      Console.WriteLine(num);
  }
  ```
- Lambda expressions improve code readability and are a key feature of LINQ and functional programming in C#.

**50. What are asynchronous streams in C# and how are they used?**
- Asynchronous streams allow for asynchronous iteration over a sequence of values.
- They are implemented using `IAsyncEnumerable<T>` and `await foreach`.
- Example:
  ```csharp
  public async IAsyncEnumerable<int> GetNumbersAsync() {
      for (int i = 0; i < 5; i++) {
          await Task.Delay(1000);
          yield return i;
      }
  }
  
  public async Task ConsumeNumbersAsync() {
      await foreach (var number in GetNumbersAsync()) {
          Console.WriteLine(number);
      }
  }
  ```
- Asynchronous streams enable efficient processing of data that is produced asynchronously, such as data from a network stream or user input.
- They improve responsiveness and scalability by allowing other work to be performed while waiting for the next value.
- `await foreach` is used to consume asynchronous streams, providing a familiar syntax similar to synchronous iteration.
