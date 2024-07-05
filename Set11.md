### Set 11:

**51. What are expression-bodied members in C# and how are they used?**
- Expression-bodied members provide a concise syntax for methods, properties, constructors, and destructors that consist of a single expression.
- They use the `=>` operator followed by the expression.
- Example for a method:
  ```csharp
  public class Example {
      public int Add(int a, int b) => a + b;
  }
  ```
- Example for a property:
  ```csharp
  public class Example {
      private int _value;
      public int Value {
          get => _value;
          set => _value = value;
      }
  }
  ```
- Expression-bodied members improve readability and reduce boilerplate code.
- They are useful for simple operations where the full method or property syntax would be unnecessarily verbose.

**52. What are value tuples in C# and how are they different from reference tuples?**
- Value tuples are simple, immutable data structures that can hold multiple elements.
- They are defined using the `System.ValueTuple` namespace and provide a lightweight alternative to creating custom classes or structs.
- Example:
  ```csharp
  var person = (1, "John Doe", 30);
  Console.WriteLine($"ID: {person.Item1}, Name: {person.Item2}, Age: {person.Item3}");
  ```
- Value tuples are value types, meaning they are allocated on the stack and provide better performance for temporary data.
- Reference tuples, provided by the `Tuple<T1, T2, ...>` class, are reference types allocated on the heap.
- Example of a reference tuple:
  ```csharp
  var person = Tuple.Create(1, "John Doe", 30);
  Console.WriteLine($"ID: {person.Item1}, Name: {person.Item2}, Age: {person.Item3}");
  ```
- Value tuples have a simpler syntax and support deconstruction, making them more convenient for many scenarios.

**53. What are nullable reference types in C# and how do they help with null safety?**
- Nullable reference types are a feature that allows developers to explicitly indicate whether a reference type can be null.
- They help catch potential `NullReferenceException` issues at compile time.
- Nullable reference types are enabled using the `#nullable` context or project-wide settings.
- Example:
  ```csharp
  #nullable enable
  public class Person {
      public string? MiddleName { get; set; }
  }
  #nullable disable
  ```
- The `?` annotation indicates that `MiddleName` can be null.
- Nullable reference types enable the compiler to enforce null safety by warning about potential null dereferences.
- This feature improves code quality and reduces runtime errors by making nullability explicit in the type system.

**54. What is the `dynamic` type in C# and when should it be used?**
- The `dynamic` type allows operations to bypass compile-time type checking and defer type resolution until runtime.
- It is used for interoperability with dynamic languages, COM objects, and scenarios where the type is not known at compile time.
- Example:
  ```csharp
  dynamic obj = "Hello, World!";
  Console.WriteLine(obj.Length); // Resolved at runtime
  ```
- The `dynamic` type can simplify code when working with reflection or dynamic data sources.
- It should be used with caution, as it sacrifices type safety and can lead to runtime errors if used improperly.
- Using `dynamic` can reduce the need for boilerplate code and improve interoperability but should be balanced with the need for type safety and performance.

**55. What are record types in C# and how do they differ from regular classes?**
- Record types provide a concise way to define immutable data objects with value-based equality semantics.
- They are designed for scenarios where the primary purpose is to store and transfer data.
- Example:
  ```csharp
  public record Person(string FirstName, string LastName);
  
  var person1 = new Person("John", "Doe");
  var person2 = new Person("John", "Doe");
  Console.WriteLine(person1 == person2); // True, value-based equality
  ```
- Record types automatically generate `Equals`, `GetHashCode`, and `ToString` methods based on their properties.
- They support positional syntax, making it easy to create and deconstruct instances.
- Unlike regular classes, records are immutable by default and emphasize value-based equality rather than reference equality.
- 
