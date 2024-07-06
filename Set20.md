### Set 20:

**111. What is the `sealed` keyword in C# and how is it used?**
- The `sealed` keyword prevents a class from being inherited or a method from being overridden.
- It is used to ensure that a class or method cannot be further extended or modified.
- Example:
  ```csharp
  public sealed class SealedClass {
      public void Display() {
          Console.WriteLine("SealedClass Display method");
      }
  }

  // Attempting to inherit SealedClass will result in a compile-time error.
  // public class DerivedClass : SealedClass { }

  public class BaseClass {
      public virtual void Show() {
          Console.WriteLine("BaseClass Show method");
      }
  }

  public class DerivedClass : BaseClass {
      public sealed override void Show() {
          Console.WriteLine("DerivedClass Show method");
      }
  }

  // Further inheritance will prevent overriding of the sealed method.
  // public class FurtherDerivedClass : DerivedClass {
  //     public override void Show() { } // Compile-time error
  // }
  ```
- `sealed` is used for security and performance reasons, ensuring certain behavior or preventing changes in sensitive classes or methods.
- It provides a way to finalize the implementation of a class or method.
- Proper use of `sealed` enhances code stability and prevents unintended modifications.

**112. What is the difference between `IEnumerable` and `IQueryable` in C#?**
- `IEnumerable` is used for in-memory collection traversal, providing forward-only iteration over a collection.
  ```csharp
  List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
  IEnumerable<int> enumerable = numbers.Where(n => n > 2);
  foreach (int number in enumerable) {
      Console.WriteLine(number);
  }
  ```
- `IQueryable` is used for querying data from out-of-memory data sources like databases, supporting deferred execution and remote querying.
  ```csharp
  IQueryable<int> queryable = dbContext.Numbers.Where(n => n > 2);
  foreach (int number in queryable) {
      Console.WriteLine(number);
  }
  ```
- `IEnumerable` executes queries immediately and fully in memory.
- `IQueryable` translates queries into the data source's native query language (e.g., SQL) and executes them on the server side.
- `IEnumerable` is suitable for LINQ to Objects, while `IQueryable` is suitable for LINQ to SQL or LINQ to Entities.
- Proper use of `IEnumerable` and `IQueryable` optimizes performance and resource usage based on data source and query requirements.

**113. What is covariance and contravariance in C#?**
- Covariance allows a method to return a more derived type than specified by the generic parameter.
  ```csharp
  public delegate Animal CovariantDelegate();
  public class Animal { }
  public class Dog : Animal { }

  CovariantDelegate del = () => new Dog();
  Animal animal = del();
  ```
- Contravariance allows a method to accept parameters of a less derived type than specified by the generic parameter.
  ```csharp
  public delegate void ContravariantDelegate(Dog dog);

  ContravariantDelegate del = (Animal animal) => { };
  del(new Dog());
  ```
- Covariance and contravariance are supported in generic interfaces and delegates using `out` and `in` keywords respectively.
  ```csharp
  public interface ICovariant<out T> {
      T Get();
  }

  public interface IContravariant<in T> {
      void Set(T item);
  }
  ```
- Covariance and contravariance enhance flexibility in generic programming, allowing for more reusable and type-safe code.
- They are particularly useful in scenarios involving inheritance hierarchies and polymorphism.
- Proper use of covariance and contravariance improves code readability, maintainability, and type safety.

**114. What is a destructor in C# and how is it used?**
- A destructor is a method that is called when an object is being garbage collected, allowing for cleanup operations.
- It is defined using a tilde (`~`) followed by the class name.
- Example:
  ```csharp
  public class Example {
      ~Example() {
          // Cleanup code
          Console.WriteLine("Destructor called");
      }
  }

  var example = new Example();
  example = null;
  GC.Collect();
  GC.WaitForPendingFinalizers();
  ```
- Destructors cannot be called explicitly and have no parameters or return type.
- They are typically used to release unmanaged resources or perform other cleanup tasks.
- Proper use of destructors ensures that resources are released when objects are no longer needed, preventing resource leaks.

**115. What is an `Action` delegate in C# and how is it used?**
- An `Action` delegate represents a method that takes zero or more parameters and does not return a value.
- It is part of the `System` namespace and can have up to 16 parameters.
- Example:
  ```csharp
  Action<int, int> add = (x, y) => Console.WriteLine(x + y);
  add(3, 4); // Outputs 7

  Action<string> greet = (name) => Console.WriteLine($"Hello, {name}");
  greet("World"); // Outputs "Hello, World"
  ```
- `Action` delegates provide a way to encapsulate methods with specific signatures without defining custom delegate types.
- They improve code readability and reduce the need for boilerplate code.
- Proper use of `Action` delegates enhances flexibility and reusability in event handling, callbacks, and functional programming.

**116. What is a `Func` delegate in C# and how is it used?**
- A `Func` delegate represents a method that takes zero or more parameters and returns a value.
- It is part of the `System` namespace and can have up to 16 parameters, with the last parameter representing the return type.
- Example:
  ```csharp
  Func<int, int, int> add = (x, y) => x + y;
  int result = add(3, 4); // Outputs 7

  Func<string, int> getLength = (str) => str.Length;
  int length = getLength("Hello"); // Outputs 5
  ```
- `Func` delegates provide a way to encapsulate methods with specific signatures without defining custom delegate types.
- They improve code readability and reduce the need for boilerplate code.
- Proper use of `Func` delegates enhances flexibility and reusability in event handling, callbacks, and functional programming.

**117. What is the difference between `StringBuilder` and `String` in C#?**
- `StringBuilder` is a mutable class for efficiently manipulating strings, while `String` is immutable.
  ```csharp
  StringBuilder sb = new StringBuilder("Hello");
  sb.Append(" World");
  Console.WriteLine(sb.ToString()); // Outputs "Hello World"

  string str = "Hello";
  str += " World";
  Console.WriteLine(str); // Outputs "Hello World"
  ```
- `StringBuilder` is optimized for scenarios involving frequent or extensive string modifications.
- `String` creates a new object for each modification, leading to performance overhead in scenarios with many changes.
- `StringBuilder` methods modify the existing instance, reducing memory allocations and improving performance.
- Proper use of `StringBuilder` enhances performance and resource efficiency in string manipulation tasks.

**118. What is the `Path` class in C# and how is it used?**
- The `Path` class provides methods for manipulating and obtaining information about file and directory paths.
- It is part of the `System.IO` namespace and includes methods for combining, retrieving, and parsing paths.
- Example:
  ```csharp
  string fullPath = Path.Combine("C:\\Folder", "file.txt");
  Console.WriteLine(fullPath); // Outputs "C:\Folder\file.txt"

  string directory = Path.GetDirectoryName(fullPath);
  string fileName = Path.GetFileName(fullPath);
  string extension = Path.GetExtension(fullPath);

  Console.WriteLine(directory); // Outputs "C:\Folder"
  Console.WriteLine(fileName); // Outputs "file.txt"
  Console.WriteLine(extension); // Outputs ".txt"
  ```
- The `Path` class helps ensure that file and directory paths are correctly formatted and platform-independent.
- It provides methods for common path operations, improving code readability and reducing errors.
- Proper use of the `Path` class enhances file and directory management in applications.

**119. What is a `custom attribute` in C# and how is it implemented?**
- A custom attribute is a user-defined attribute that can be applied to classes, methods, properties, and other program elements.
- It is created by defining a class that inherits from `System.Attribute`.
- Example:
  ```csharp
  [AttributeUsage(AttributeTargets.Class | AttributeTargets.Method)]
  public class AuthorAttribute : Attribute {
      public string Name { get; }
      public AuthorAttribute(string name) {
          Name = name;
      }
  }

  [Author("John Doe")]
  public class SampleClass {
      [Author("Jane Doe")]
      public void SampleMethod() {
          Console.WriteLine("Method with custom attribute");
      }
  }
  ```
- Custom attributes allow attaching metadata to program elements, which can be accessed using reflection.
- They are useful for adding descriptive information, enforcing rules, or providing additional context.
- Proper use of custom attributes enhances code readability, maintainability, and flexibility by allowing metadata-driven behavior.

**120. What is the difference between `Task` and `Thread` in C#?**
- `Task` represents an asynchronous operation that can run on

 a thread pool thread, whereas `Thread` represents a single unit of execution.
  ```csharp
  Task.Run(() => Console.WriteLine("Task running"));
  
  Thread thread = new Thread(() => Console.WriteLine("Thread running"));
  thread.Start();
  ```
- `Task` supports higher-level constructs for parallel and asynchronous programming, including continuations and cancellation.
- `Thread` provides lower-level control over thread lifecycle, priority, and synchronization.
- `Task` is more efficient for short-lived or many concurrent operations, utilizing the thread pool for optimal resource management.
- `Thread` is suitable for long-running or background operations requiring dedicated threads.
- Proper use of `Task` and `Thread` enhances performance, scalability, and maintainability in multi-threaded and asynchronous applications.
