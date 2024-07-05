### Set 6:

**26. What is the purpose of attributes in C#?**
- Attributes provide a powerful method of associating metadata or declarative information with code.
- They can be applied to assemblies, classes, methods, properties, and other program elements.
- Attributes are used for various purposes, including specifying behavior, enforcing rules, and documentation.
- Example:
  ```csharp
  [Obsolete("Use NewMethod instead")]
  public void OldMethod() {
      // Method logic
  }
  ```
- Custom attributes can be created by deriving from the `System.Attribute` class.
- Attributes are accessed through reflection at runtime, allowing for dynamic behavior based on attribute data.

**27. Explain the concept of `async` and `await` in C#.**
- `async` and `await` keywords are used to write asynchronous code.
- The `async` keyword is applied to a method to indicate that it contains asynchronous operations.
- The `await` keyword is used to suspend the execution of an async method until the awaited task completes.
- Example:
  ```csharp
  public async Task<int> GetDataAsync() {
      await Task.Delay(1000); // Simulate asynchronous operation
      return 42;
  }
  ```
- Asynchronous methods allow for non-blocking execution, improving application responsiveness and scalability.
- The `await` keyword can only be used inside methods marked with the `async` keyword.

**28. What is LINQ in C# and why is it useful?**
- LINQ (Language Integrated Query) is a set of features for querying data in a more readable and concise manner.
- LINQ provides a consistent model for working with different data sources, including in-memory collections, databases, XML, and more.
- Example:
  ```csharp
  int[] numbers = { 1, 2, 3, 4, 5 };
  var evenNumbers = from n in numbers
                    where n % 2 == 0
                    select n;
  ```
- LINQ syntax includes query expressions and method syntax.
- It enhances code readability and maintainability by allowing queries to be written directly in C#.
- LINQ leverages strong typing, IntelliSense, and compile-time checking, reducing errors and improving productivity.

**29. What are generics in C# and how do they work?**
- Generics allow for the definition of classes, methods, and data structures with a placeholder for the type of data they store or use.
- They provide type safety without compromising performance by enabling code reuse.
- Example of a generic class:
  ```csharp
  public class GenericList<T> {
      private T[] items = new T[10];
      public void Add(T item) {
          // Add item to list
      }
      public T Get(int index) {
          return items[index];
      }
  }
  ```
- Example of a generic method:
  ```csharp
  public T GenericMethod<T>(T input) {
      return input;
  }
  ```
- Generics improve code reusability, type safety, and performance by avoiding boxing and unboxing.
- They are extensively used in collections (e.g., `List<T>`, `Dictionary<TKey, TValue>`) and various other .NET features.

**30. Explain the `nullable` types in C# and how they are used.**
- Nullable types allow value types to represent `null` values.
- Nullable types are declared using the `?` syntax or `Nullable<T>`.
- Example:
  ```csharp
  int? nullableInt = null;
  if (nullableInt.HasValue) {
      Console.WriteLine(nullableInt.Value);
  } else {
      Console.WriteLine("Value is null");
  }
  ```
- They are useful for representing optional or missing data, such as database fields that may have null values.
- Nullable types provide properties and methods (`HasValue`, `Value`, `GetValueOrDefault()`) to safely work with potentially null values.
- They are widely used in scenarios where value types need to accommodate the possibility of null values, enhancing flexibility and robustness.
