### Set 18:

**91. What is the `lock` statement in C# and how is it used?**
- The `lock` statement is used to ensure that a block of code runs exclusively by a single thread, providing thread synchronization.
- It prevents race conditions by locking a particular object until the code block is finished executing.
- Example:
  ```csharp
  public class Counter {
      private int count = 0;
      private readonly object lockObject = new object();

      public void Increment() {
          lock (lockObject) {
              count++;
          }
      }

      public int GetCount() {
          return count;
      }
  }
  ```
- The `lock` statement requires a reference type as its parameter.
- It helps maintain data integrity and consistency in multi-threaded applications.
- Using `lock` properly prevents deadlocks and performance issues caused by excessive locking.

**92. What is the difference between `abstract class` and `interface` in C#?**
- An `abstract class` can provide both abstract methods (without implementation) and concrete methods (with implementation).
  ```csharp
  public abstract class Animal {
      public abstract void MakeSound();
      public void Sleep() {
          Console.WriteLine("Sleeping...");
      }
  }
  ```
- An `interface` can only declare methods, properties, events, or indexers without any implementation.
  ```csharp
  public interface IAnimal {
      void MakeSound();
  }
  ```
- An abstract class supports fields, constructors, and destructors, while an interface does not.
- A class can inherit only one abstract class but can implement multiple interfaces.
- Abstract classes are used for shared code and default behavior, while interfaces define contracts for classes to implement.

**93. What is the `using` statement in C# and how is it used?**
- The `using` statement ensures that `IDisposable` objects are disposed of properly, releasing resources.
- It provides a convenient syntax for managing resource lifetimes.
- Example:
  ```csharp
  using (var fileStream = new FileStream("example.txt", FileMode.Open)) {
      // Use the fileStream
  }
  // fileStream is automatically disposed of here
  ```
- The `using` statement can also be used for aliasing namespaces.
- It is important for resource management, especially for file, network, and database connections.
- Proper use of `using` ensures that resources are released promptly and helps avoid memory leaks.

**94. What is an extension method in C# and how is it implemented?**
- An extension method allows adding new methods to existing types without modifying the original type.
- It is defined as a static method in a static class, with the first parameter specifying the type to extend, prefixed with `this`.
- Example:
  ```csharp
  public static class StringExtensions {
      public static bool IsPalindrome(this string str) {
          int len = str.Length;
          for (int i = 0; i < len / 2; i++) {
              if (str[i] != str[len - i - 1]) {
                  return false;
              }
          }
          return true;
      }
  }

  string word = "madam";
  bool result = word.IsPalindrome();
  Console.WriteLine(result); // Outputs True
  ```
- Extension methods improve code readability and usability by adding methods directly to existing types.
- They are useful for extending library classes or third-party components.
- Proper use of extension methods enhances code maintainability and promotes the DRY (Don't Repeat Yourself) principle.

**95. What is the `dynamic` keyword in C# and how does it differ from `object`?**
- The `dynamic` keyword allows for late binding, deferring type checking until runtime.
- Unlike `object`, operations on `dynamic` types are resolved at runtime, bypassing compile-time type checking.
- Example:
  ```csharp
  dynamic dyn = "Hello";
  Console.WriteLine(dyn.Length); // Resolved at runtime

  dyn = 123;
  Console.WriteLine(dyn + 10); // Resolved at runtime
  ```
- The `object` type requires explicit casting to the desired type for accessing members.
- Using `dynamic` provides flexibility for interoperation with dynamic languages, COM objects, and reflection.
- `dynamic` should be used cautiously due to the lack of compile-time checking and potential for runtime errors.

**96. What is the `is` operator in C# and how is it used?**
- The `is` operator checks if an object is compatible with a given type.
- It returns `true` if the object is of the specified type or can be cast to that type; otherwise, it returns `false`.
- Example:
  ```csharp
  object obj = "Hello";
  if (obj is string str) {
      Console.WriteLine(str);
  }
  ```
- The `is` operator can be used for pattern matching with variable declaration in C# 7.0 and later.
- It simplifies type checking and casting, making code more readable and concise.
- Proper use of the `is` operator improves type safety and helps avoid runtime exceptions.

**97. What is the `as` operator in C# and how is it different from casting?**
- The `as` operator attempts to cast an object to a specified type and returns `null` if the cast fails.
- It is safer than direct casting because it does not throw an exception on failure.
- Example:
  ```csharp
  object obj = "Hello";
  string str = obj as string;
  if (str != null) {
      Console.WriteLine(str);
  }
  ```
- Direct casting throws an `InvalidCastException` if the cast is not possible.
- The `as` operator can only be used with reference types and nullable types.
- Using `as` improves code safety by handling invalid casts gracefully and avoiding exceptions.

**98. What are named and optional arguments in C# and how are they used?**
- Named arguments allow specifying arguments by their parameter names rather than by position.
  ```csharp
  void PrintMessage(string message, int count) {
      for (int i = 0; i < count; i++) {
          Console.WriteLine(message);
      }
  }

  PrintMessage(message: "Hello", count: 3);
  ```
- Optional arguments allow specifying default values for parameters, making them optional in method calls.
  ```csharp
  void PrintMessage(string message, int count = 1) {
      for (int i = 0; i < count; i++) {
          Console.WriteLine(message);
      }
  }

  PrintMessage("Hello");
  PrintMessage("Hello", 3);
  ```
- Named and optional arguments improve code readability and reduce the need for method overloads.
- They enhance method flexibility and usability by providing default behavior and self-documenting code.
- Proper use of named and optional arguments simplifies method calls and reduces parameter management overhead.

**99. What is reflection in C# and how is it used?**
- Reflection is the ability to inspect and manipulate metadata, types, and objects at runtime.
- It is commonly used for accessing type information, invoking methods, and dynamically creating instances.
- Example:
  ```csharp
  Type type = typeof(string);
  MethodInfo method = type.GetMethod("ToUpper", new Type[] { });
  string result = (string)method.Invoke("hello", null);
  Console.WriteLine(result); // Outputs "HELLO"
  ```
- Reflection enables dynamic type inspection and invocation, which is useful for frameworks, libraries, and tools.
- It can be used to load assemblies, inspect attributes, and interact with unknown types.
- Using reflection should be done with caution due to potential performance overhead and security implications.

**100. What is the `nameof` operator in C# and how is it used?**
- The `nameof` operator returns the string name of a variable, type, or member.
- It is used for refactoring-safe code, providing a way to reference names without hardcoding strings.
- Example:
  ```csharp
  public class Example {
      public int Property { get; set; }
  }

  string propertyName = nameof(Example.Property);
  Console.WriteLine(propertyName); // Outputs "Property"
  ```
- `nameof` improves code readability and maintainability, especially in logging, exceptions, and data binding.
- It helps avoid errors caused by manually typed string names and ensures that name changes are automatically updated.
