### Set 17:

**81. What is the `Nullable<T>` type in C# and how is it used?**
- `Nullable<T>` allows value types to represent null values, which is not possible with regular value types.
- It is commonly used for database fields and optional parameters where null values are allowed.
- Example:
  ```csharp
  int? nullableInt = null;
  if (nullableInt.HasValue) {
      Console.WriteLine(nullableInt.Value);
  } else {
      Console.WriteLine("Value is null");
  }
  ```
- The `HasValue` property indicates whether the nullable type has a value.
- The `Value` property retrieves the value if it is not null; otherwise, it throws an `InvalidOperationException`.
- Using `Nullable<T>` improves code flexibility and aligns with scenarios where value types can be absent.

**82. What is a delegate in C# and how is it used?**
- A delegate is a type that represents references to methods with a specific signature.
- It allows methods to be passed as parameters and enables callback functionality.
- Example:
  ```csharp
  public delegate void DisplayMessage(string message);

  public class Messenger {
      public void ShowMessage(DisplayMessage displayMessage) {
          displayMessage("Hello, World!");
      }
  }

  public static void Main() {
      Messenger messenger = new Messenger();
      messenger.ShowMessage(Console.WriteLine);
  }
  ```
- Delegates provide a way to define and call methods dynamically at runtime.
- They support multicast functionality, allowing multiple methods to be invoked by a single delegate.
- Delegates are commonly used for event handling and implementing design patterns like Observer and Strategy.

**83. What are lambda expressions in C# and how are they used?**
- Lambda expressions provide a concise way to write anonymous methods using the `=>` syntax.
- They are often used in LINQ queries and for defining delegates and expression trees.
- Example:
  ```csharp
  Func<int, int, int> add = (x, y) => x + y;
  Console.WriteLine(add(2, 3)); // Outputs 5
  ```
- Lambda expressions can have input parameters on the left side and the expression or statement block on the right side.
- They improve code readability and reduce the need for verbose anonymous method syntax.
- Lambda expressions are powerful in functional programming, event handling, and data manipulation scenarios.

**84. What is an `event` in C# and how is it implemented?**
- An `event` is a member that enables a class or object to provide notifications to other classes or objects when something of interest occurs.
- Events are based on delegates and use the `event` keyword.
- Example:
  ```csharp
  public delegate void Notify();
  public class Process {
      public event Notify ProcessCompleted;

      public void StartProcess() {
          Console.WriteLine("Process Started");
          OnProcessCompleted();
      }

      protected virtual void OnProcessCompleted() {
          ProcessCompleted?.Invoke();
      }
  }

  public class Program {
      public static void Main() {
          Process process = new Process();
          process.ProcessCompleted += ProcessCompletedHandler;
          process.StartProcess();
      }

      static void ProcessCompletedHandler() {
          Console.WriteLine("Process Completed");
      }
  }
  ```
- Events provide a way for classes to communicate with each other without tight coupling.
- They are commonly used in GUI applications, asynchronous programming, and event-driven architectures.
- Proper event handling ensures responsiveness and scalability in applications.

**85. What are generics in C# and how are they used?**
- Generics allow the definition of type-safe data structures and methods without specifying the exact data type.
- They provide type safety, code reusability, and performance benefits.
- Example:
  ```csharp
  public class GenericList<T> {
      private List<T> _items = new List<T>();
      
      public void Add(T item) {
          _items.Add(item);
      }

      public T Get(int index) {
          return _items[index];
      }
  }

  var intList = new GenericList<int>();
  intList.Add(1);
  Console.WriteLine(intList.Get(0));
  ```
- Generics are defined using angle brackets (`<T>`) and can be applied to classes, methods, interfaces, and delegates.
- They eliminate the need for casting and runtime type checking, reducing runtime errors.
- Generics improve code flexibility and maintainability by promoting reusable components.

**86. What is `yield` in C# and how is it used?**
- The `yield` keyword is used to return elements one at a time from an iterator method.
- It enables the creation of custom iterators without explicitly implementing the `IEnumerator` or `IEnumerable` interfaces.
- Example:
  ```csharp
  public IEnumerable<int> GetNumbers() {
      for (int i = 0; i < 5; i++) {
          yield return i;
      }
  }

  foreach (var number in GetNumbers()) {
      Console.WriteLine(number);
  }
  ```
- `yield return` returns the current element and pauses the method until the next iteration.
- `yield break` terminates the iteration sequence.
- Using `yield` simplifies the creation of lazy-loaded sequences and improves code readability.

**87. What is a `dynamic` type in C# and how is it used?**
- The `dynamic` type bypasses compile-time type checking, deferring type checking to runtime.
- It allows for operations that are resolved at runtime, providing flexibility for dynamic scenarios.
- Example:
  ```csharp
  dynamic dyn = "Hello";
  Console.WriteLine(dyn.Length); // Resolved at runtime

  dyn = 123;
  Console.WriteLine(dyn + 10); // Resolved at runtime
  ```
- `dynamic` is useful for working with COM objects, dynamic languages, and scenarios where the type is not known until runtime.
- It enables interoperability with APIs that do not have static type definitions.
- Using `dynamic` should be done cautiously as it can lead to runtime errors and reduced performance.

**88. What is the `params` keyword in C# and how is it used?**
- The `params` keyword allows a method to accept a variable number of arguments as an array.
- It provides flexibility for methods that require an unspecified number of parameters.
- Example:
  ```csharp
  public void PrintNumbers(params int[] numbers) {
      foreach (var number in numbers) {
          Console.WriteLine(number);
      }
  }

  PrintNumbers(1, 2, 3, 4, 5);
  ```
- `params` must be the last parameter in the method signature.
- It simplifies method calls by allowing a varying number of arguments without manually creating an array.
- `params` is useful for methods like logging, aggregation, and formatting where the number of inputs can vary.

**89. What is a `predicate` in C# and how is it used?**
- A predicate is a delegate that defines a set of criteria and determines whether the specified object meets those criteria.
- It is represented by the `Predicate<T>` delegate, which returns a boolean value.
- Example:
  ```csharp
  List<int> numbers = new List<int> { 1, 2, 3, 4, 5 };
  Predicate<int> isEven = x => x % 2 == 0;
  
  List<int> evenNumbers = numbers.FindAll(isEven);
  evenNumbers.ForEach(Console.WriteLine);
  ```
- Predicates are commonly used with collection methods like `Find`, `FindAll`, `Exists`, and `RemoveAll`.
- They encapsulate the logic for filtering, searching, and matching elements in a collection.
- Using predicates improves code readability and reusability by separating the criteria from the collection operations.

**90. What is method overloading in C# and how is it implemented?**
- Method overloading allows multiple methods with the same name but different parameters to coexist in the same class.
- It enables methods to handle different types or numbers of inputs.
- Example:
  ```csharp
  public class Calculator {
      public int Add(int a, int b) {
          return a + b;
      }

      public double Add(double a, double b) {
          return a + b;
      }

      public int Add(int a, int b, int c) {
          return a + b + c;
      }
  }

  Calculator calc = new Calculator();
  Console.WriteLine(calc.Add(1, 2)); // Outputs 3
  Console.WriteLine(calc.Add(1.5, 2.5)); // Outputs 4.0
  Console.WriteLine(calc.Add(1, 2, 3)); // Outputs 6
  ```
- Overloaded methods must differ in the number or type of parameters but can share the same name.
- Method overloading improves code flexibility and readability by providing different ways to perform similar operations.
- It helps avoid the need for method names that describe every possible combination of parameters.

Would you like another set?
