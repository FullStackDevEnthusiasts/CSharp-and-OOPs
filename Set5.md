### Set 5:

**21. What is the difference between `const` and `readonly` in C#?**
- `const` is used to declare constants, which are immutable and must be assigned at compile time.
- `readonly` is used to declare fields that can only be assigned during declaration or in a constructor, allowing for runtime assignment.
- `const` fields are static by default and their values cannot change.
- Example of `const`: `public const int MaxValue = 100;`
- Example of `readonly`: 
  ```csharp
  public readonly int maxValue;
  public MyClass(int value) {
      maxValue = value;
  }
  ```
- `const` is used for values that are known at compile time and will not change, while `readonly` is used for values that are determined at runtime.

**22. What is the purpose of the `new` keyword in C#?**
- The `new` keyword is used for object creation.
- Example: `MyClass obj = new MyClass();`
- It is also used to hide a member of a base class with a new implementation in a derived class.
- Example:
  ```csharp
  class BaseClass {
      public void Display() {
          Console.WriteLine("Base Display");
      }
  }
  class DerivedClass : BaseClass {
      public new void Display() {
          Console.WriteLine("Derived Display");
      }
  }
  ```
- The `new` keyword can be used with types to create instances and with methods to hide base class methods.
- It signifies that the derived class method is intentionally hiding the base class method.

**23. What is a namespace in C# and why is it used?**
- A namespace is a container for classes, structs, enums, delegates, and interfaces.
- It helps organize code and prevent naming conflicts by providing a way to group related types.
- Example:
  ```csharp
  namespace MyNamespace {
      class MyClass {
          public void MyMethod() {
              Console.WriteLine("Hello, Namespace!");
          }
      }
  }
  ```
- Namespaces can be nested, allowing for hierarchical organization of code.
- The `using` directive is used to import namespaces into a file for easier access to their members.
- Namespaces provide a way to logically separate code and manage dependencies.

**24. Explain the concept of garbage collection in C#.**
- Garbage collection (GC) is an automatic memory management feature in .NET.
- It helps to reclaim memory occupied by objects that are no longer in use.
- The GC operates in three main phases: marking, relocating, and compacting.
- It identifies objects that are still reachable and marks them, then relocates surviving objects, and finally compacts the heap by removing gaps left by reclaimed objects.
- Developers can influence GC behavior using methods like `GC.Collect()`, but explicit calls are generally discouraged.
- The GC improves memory efficiency and reduces memory leaks, but can introduce performance overhead due to collection cycles.

**25. What are extension methods in C# and how are they implemented?**
- Extension methods allow adding new methods to existing types without modifying their source code.
- They are defined as static methods in static classes and use the `this` keyword in the first parameter to specify the type they extend.
- Example:
  ```csharp
  public static class StringExtensions {
      public static bool IsPalindrome(this string str) {
          int len = str.Length;
          for (int i = 0; i < len / 2; i++) {
              if (str[i] != str[len - i - 1]) return false;
          }
          return true;
      }
  }
  ```
- Usage:
  ```csharp
  string s = "level";
  bool result = s.IsPalindrome(); // Calls the extension method
  ```
- Extension methods enhance the functionality of existing types, making code more readable and maintainable.
- They are commonly used to add utility methods to built-in types and third-party libraries.
