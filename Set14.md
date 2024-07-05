
### Set 14:

**66. What are anonymous types in C# and how are they used?**
- Anonymous types provide a way to encapsulate a set of read-only properties into a single object without having to explicitly define a class.
- They are useful for temporary data structures, especially in LINQ queries.
- Example:
  ```csharp
  var person = new { FirstName = "John", LastName = "Doe" };
  Console.WriteLine($"First Name: {person.FirstName}, Last Name: {person.LastName}");
  ```
- Anonymous types are created using the `new` keyword followed by an object initializer.
- The properties of anonymous types are read-only and inferred from the values provided.
- Anonymous types improve code readability and reduce the need for boilerplate code when working with temporary data.

**67. What is `Task` in C# and how is it used for asynchronous programming?**
- `Task` represents an asynchronous operation and is part of the Task Parallel Library (TPL).
- It provides a way to run code asynchronously and manage its completion.
- Example:
  ```csharp
  public async Task<int> FetchDataAsync() {
      await Task.Delay(1000); // Simulate async work
      return 42;
  }
  
  public async Task MainAsync() {
      int result = await FetchDataAsync();
      Console.WriteLine(result);
  }
  ```
- `Task` supports continuation, cancellation, and exception handling.
- It is used with the `async` and `await` keywords to simplify asynchronous programming.
- Using `Task` improves application responsiveness and scalability by allowing non-blocking operations.

**68. What are extension methods in C# and how are they implemented?**
- Extension methods allow adding new methods to existing types without modifying the original type or creating a new derived type.
- They are defined as static methods in static classes and use the `this` keyword as the first parameter.
- Example:
  ```csharp
  public static class StringExtensions {
      public static bool IsNullOrEmpty(this string str) {
          return string.IsNullOrEmpty(str);
      }
  }
  
  string example = "Hello";
  bool isEmpty = example.IsNullOrEmpty(); // Using the extension method
  ```
- Extension methods improve code readability and reusability by allowing natural method syntax on existing types.
- They are commonly used for LINQ and other utility methods.
- Extension methods cannot override existing methods or access private members of the type.

**69. What is the difference between `Array` and `List` in C#?**
- `Array` is a fixed-size, zero-based collection of elements of the same type.
- `List<T>` is a dynamic-size collection that can grow and shrink as needed.
- Example of an array:
  ```csharp
  int[] numbers = new int[5];
  numbers[0] = 1;
  ```
- Example of a list:
  ```csharp
  List<int> numbers = new List<int>();
  numbers.Add(1);
  numbers.Add(2);
  ```
- Arrays provide better performance for fixed-size collections due to their simpler structure.
- Lists offer more flexibility with dynamic resizing, and they provide a richer set of methods for manipulation.
- Lists are often preferred for collections where the size may change during the program's execution.

**70. What is the `this` keyword in C# and how is it used?**
- The `this` keyword refers to the current instance of the class.
- It is used to access members and methods of the current object and to distinguish between instance variables and parameters with the same name.
- Example:
  ```csharp
  public class Example {
      private int _value;
      
      public void SetValue(int value) {
          this._value = value; // Using `this` to distinguish between the field and parameter
      }
  }
  ```
- The `this` keyword is also used in extension methods to refer to the extended type.
- It can be used in constructors to call another constructor in the same class.
- Using `this` improves code clarity and helps avoid naming conflicts.
