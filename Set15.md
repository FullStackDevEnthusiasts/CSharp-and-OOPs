### Set 15:

**71. What are partial classes in C# and how are they used?**
- Partial classes allow a class to be split into multiple files, enabling collaborative development and separating concerns.
- Each part of the partial class must use the `partial` keyword.
- Example:
  ```csharp
  // File: Part1.cs
  public partial class Example {
      public void Method1() {
          Console.WriteLine("Method1");
      }
  }

  // File: Part2.cs
  public partial class Example {
      public void Method2() {
          Console.WriteLine("Method2");
      }
  }

  // Usage
  Example ex = new Example();
  ex.Method1();
  ex.Method2();
  ```
- Partial classes are combined into a single class during compilation.
- They are useful for separating auto-generated code from manually written code.
- Partial classes improve code organization and maintainability.

**72. What is the difference between `public`, `private`, `protected`, and `internal` access modifiers in C#?**
- `public`: The member is accessible from any other code.
  ```csharp
  public class Example {
      public int PublicField;
  }
  ```
- `private`: The member is accessible only within the containing class.
  ```csharp
  public class Example {
      private int PrivateField;
  }
  ```
- `protected`: The member is accessible within the containing class and by derived classes.
  ```csharp
  public class Example {
      protected int ProtectedField;
  }
  ```
- `internal`: The member is accessible only within the same assembly.
  ```csharp
  internal class Example {
      internal int InternalField;
  }
  ```
- `protected internal`: The member is accessible within the same assembly and by derived classes.
  ```csharp
  public class Example {
      protected internal int ProtectedInternalField;
  }
  ```
- Access modifiers control the visibility and accessibility of class members, improving encapsulation and security.

**73. What is an indexer in C# and how is it implemented?**
- An indexer allows objects to be indexed like arrays, providing a way to access elements using a subscript notation.
- Example:
  ```csharp
  public class SampleCollection<T> {
      private T[] arr = new T[100];
      public T this[int i] {
          get => arr[i];
          set => arr[i] = value;
      }
  }

  var collection = new SampleCollection<string>();
  collection[0] = "Hello";
  Console.WriteLine(collection[0]);
  ```
- Indexers are defined using the `this` keyword followed by parameters in square brackets.
- They can be overloaded with multiple parameters to support multi-dimensional indexing.
- Indexers improve the usability of custom collections and enhance the intuitive use of objects.

**74. What is a `sealed` class in C# and why would you use one?**
- A `sealed` class cannot be inherited, preventing other classes from deriving from it.
- Example:
  ```csharp
  public sealed class SealedClass {
      public void Method() {
          Console.WriteLine("Method in SealedClass");
      }
  }
  ```
- Sealing a class can improve performance because it allows the runtime to make optimizations.
- It is used when you want to restrict the inheritance to ensure the integrity of the class's implementation.
- Sealed classes are often used in conjunction with utility or helper classes that should not be extended.

**75. What is the difference between `Task.Run` and `Task.Factory.StartNew` in C#?**
- `Task.Run` is a higher-level method for creating and running a task using the default task scheduler and default settings.
  ```csharp
  Task.Run(() => {
      // Task code
  });
  ```
- `Task.Factory.StartNew` provides more control over task creation options, including scheduling, task state, and cancellation.
  ```csharp
  Task.Factory.StartNew(() => {
      // Task code
  }, CancellationToken.None, TaskCreationOptions.None, TaskScheduler.Default);
  ```
- `Task.Run` is typically used for simple scenarios where default settings are sufficient.
- `Task.Factory.StartNew` is used when advanced options or custom settings are required.
- `Task.Run` implicitly uses `TaskCreationOptions.DenyChildAttach`, preventing child tasks from attaching to the parent task, while `Task.Factory.StartNew` does not.

