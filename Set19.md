### Set 19:

**101. What is the `volatile` keyword in C# and how is it used?**
- The `volatile` keyword indicates that a field can be modified by multiple threads without compiler optimizations that assume the field is not changed unexpectedly.
- It ensures that the most recent value is always read and written to memory.
- Example:
  ```csharp
  public class Example {
      private volatile bool _stop;

      public void Stop() {
          _stop = true;
      }

      public void Run() {
          while (!_stop) {
              // Do work
          }
      }
  }
  ```
- `volatile` is used for fields accessed by multiple threads, ensuring visibility and preventing stale values.
- It provides a lightweight synchronization mechanism but does not offer atomicity or mutual exclusion.
- Proper use of `volatile` improves the correctness of multi-threaded applications by ensuring up-to-date values.

**102. What is a `readonly` field in C# and how does it differ from `const`?**
- A `readonly` field can only be assigned a value during declaration or in the constructor of the same class.
  ```csharp
  public class Example {
      public readonly int ReadOnlyField;

      public Example(int value) {
          ReadOnlyField = value;
      }
  }
  ```
- A `const` field is a compile-time constant and must be assigned a value at the time of declaration.
  ```csharp
  public class Example {
      public const int ConstField = 10;
  }
  ```
- `readonly` fields can have different values for different instances, while `const` fields have the same value for all instances.
- `readonly` fields can be used with reference types and mutable objects, whereas `const` fields are limited to primitive data types and immutable objects.
- `readonly` provides flexibility for instance-specific constants, while `const` ensures compile-time constants.

**103. What is the `ThreadStatic` attribute in C# and how is it used?**
- The `ThreadStatic` attribute indicates that the value of a static field is unique for each thread.
- It is used to create thread-local storage for static fields.
- Example:
  ```csharp
  public class Example {
      [ThreadStatic]
      private static int _threadSpecificData;

      public static void SetData(int value) {
          _threadSpecificData = value;
      }

      public static int GetData() {
          return _threadSpecificData;
      }
  }
  ```
- Fields marked with `ThreadStatic` have separate instances for each thread, ensuring thread-specific data.
- It is useful for scenarios where data should not be shared between threads, such as caching or thread-local counters.
- Proper use of `ThreadStatic` improves thread safety and isolation, preventing unintended data sharing.

**104. What is the `Lazy<T>` class in C# and how is it used?**
- The `Lazy<T>` class provides a way to defer the initialization of an object until it is needed, known as lazy initialization.
- It improves performance by delaying the creation of resource-intensive objects.
- Example:
  ```csharp
  public class Example {
      private readonly Lazy<ExpensiveObject> _lazyObject = new Lazy<ExpensiveObject>(() => new ExpensiveObject());

      public ExpensiveObject GetObject() {
          return _lazyObject.Value;
      }
  }

  public class ExpensiveObject {
      public ExpensiveObject() {
          Console.WriteLine("ExpensiveObject created");
      }
  }
  ```
- The `Lazy<T>` instance ensures that the object is created only once and only when accessed.
- It supports thread-safety and lazy initialization patterns.
- Using `Lazy<T>` improves performance and resource management by avoiding unnecessary object creation.

**105. What is the `WeakReference` class in C# and how is it used?**
- The `WeakReference` class allows an object to be referenced without preventing it from being collected by garbage collection.
- It is used to handle memory-sensitive scenarios where objects should be eligible for garbage collection when no strong references exist.
- Example:
  ```csharp
  public class Example {
      private WeakReference<ExpensiveObject> _weakRef;

      public void SetObject(ExpensiveObject obj) {
          _weakRef = new WeakReference<ExpensiveObject>(obj);
      }

      public ExpensiveObject GetObject() {
          if (_weakRef.TryGetTarget(out ExpensiveObject target)) {
              return target;
          }
          return null;
      }
  }

  public class ExpensiveObject {
      public ExpensiveObject() {
          Console.WriteLine("ExpensiveObject created");
      }
  }
  ```
- `WeakReference` helps manage memory usage by allowing objects to be collected when they are no longer strongly referenced.
- It is useful for caching, event handling, and scenarios where memory management is critical.
- Proper use of `WeakReference` prevents memory leaks and optimizes resource utilization.

**106. What is a partial class in C# and how is it used?**
- A partial class allows the definition of a class to be split across multiple files.
- It enables multiple developers to work on the same class and separates code into manageable sections.
- Example:
  ```csharp
  // File1.cs
  public partial class Example {
      public void Method1() {
          Console.WriteLine("Method1");
      }
  }

  // File2.cs
  public partial class Example {
      public void Method2() {
          Console.WriteLine("Method2");
      }
  }
  ```
- All parts of a partial class must be defined with the `partial` keyword and share the same accessibility, namespace, and class name.
- Partial classes are useful for code organization, auto-generated code, and separating business logic from user interface code.
- They enhance collaboration, code readability, and maintainability in large projects.

**107. What is a `Tuple` in C# and how is it used?**
- A `Tuple` is a data structure that can hold a fixed number of items of different types.
- It is used to group multiple values into a single object without creating a separate class.
- Example:
  ```csharp
  var tuple = Tuple.Create(1, "Hello", true);
  Console.WriteLine(tuple.Item1); // Outputs 1
  Console.WriteLine(tuple.Item2); // Outputs "Hello"
  Console.WriteLine(tuple.Item3); // Outputs True
  ```
- `Tuple` supports up to eight elements, and for more elements, `ValueTuple` or custom types are recommended.
- `Tuple` improves code readability and simplifies method return values and parameter passing for multiple values.
- Using `Tuple` enhances type safety and reduces the need for temporary classes or structures.

**108. What is the `default` keyword in C# and how is it used?**
- The `default` keyword returns the default value of a type.
- For reference types, the default value is `null`, and for value types, it is the zero-initialized value.
- Example:
  ```csharp
  int defaultInt = default(int); // Outputs 0
  string defaultString = default(string); // Outputs null
  ```
- In C# 7.1 and later, the `default` keyword can be used without specifying the type.
  ```csharp
  int defaultInt = default; // Outputs 0
  string defaultString = default; // Outputs null
  ```
- `default` is useful for initializing variables, handling generic types, and providing default case values in switch statements.
- Using `default` improves code clarity and consistency by explicitly defining default values.

**109. What is an indexer in C# and how is it implemented?**
- An indexer allows instances of a class or struct to be indexed like arrays, providing array-like access to data.
- It is defined using the `this` keyword with a parameter list.
- Example:
  ```csharp
  public class SampleCollection<T> {
      private T[] arr = new T[100];

      public T this[int i] {
          get { return arr[i]; }
          set { arr[i] = value; }
      }
  }

  var collection = new SampleCollection<string>();
  collection[0] = "Hello";
  Console.WriteLine(collection[0]); // Outputs "Hello"
  ```
- Indexers can have multiple parameters and can be overloaded.
- They are useful for creating custom collections, data structures, and providing intuitive access to internal data.
- Proper use of indexers enhances code readability and usability by simplifying data access patterns.

**110. What is a `Params` array in C# and how is it used?**
- The `params` keyword allows a method to accept a variable number of arguments as an array.
- It simplifies method calls by allowing a varying number of arguments without manually creating an array.
- Example:
  ```csharp
  public void PrintNumbers(params int[] numbers) {
      foreach (var number in numbers) {
          Console.WriteLine(number);
      }
  }

  PrintNumbers(1, 2, 3, 4, 5);
  ```
- The `params` array must be the last parameter in the method signature.
- It enhances method flexibility and usability by supporting a dynamic number of inputs.
- Using `params` improves code readability and reduces the need for multiple method overloads.
