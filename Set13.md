### Set 13:

**61. What is covariance and contravariance in C# and how are they used?**
- Covariance and contravariance allow for more flexible assignment compatibility between types, especially in generic collections and delegates.
- Covariance allows a method to return a more derived type than specified by the generic parameter.
- Contravariance allows a method to accept a parameter of a less derived type than specified by the generic parameter.
- Covariance example with interfaces:
  ```csharp
  IEnumerable<string> strings = new List<string>();
  IEnumerable<object> objects = strings; // Covariance
  ```
- Contravariance example with delegates:
  ```csharp
  Action<object> actObject = obj => Console.WriteLine(obj);
  Action<string> actString = actObject; // Contravariance
  actString("Hello, World!");
  ```
- Covariance and contravariance are useful for working with collections, events, and delegates where type flexibility is needed.

**62. What is reflection in C# and how is it used?**
- Reflection is a mechanism that allows inspection of metadata and dynamic invocation of types and members at runtime.
- It is used for examining assemblies, types, properties, methods, and events.
- Example:
  ```csharp
  Type type = typeof(Person);
  Console.WriteLine("Properties of Person:");
  foreach (var prop in type.GetProperties()) {
      Console.WriteLine(prop.Name);
  }
  ```
- Reflection enables dynamic type creation, method invocation, and attribute retrieval.
- It is used in scenarios such as serialization, deserialization, and dependency injection frameworks.
- Reflection should be used judiciously as it can impact performance and security if not managed properly.

**63. What are default interface methods in C# and how are they used?**
- Default interface methods allow interfaces to provide a default implementation for their members.
- They enable interface evolution without breaking existing implementations.
- Example:
  ```csharp
  public interface IExample {
      void Method();
      void DefaultMethod() => Console.WriteLine("Default implementation");
  }
  
  public class Example : IExample {
      public void Method() {
          Console.WriteLine("Implemented Method");
      }
  }
  
  IExample example = new Example();
  example.Method();
  example.DefaultMethod(); // Calls the default implementation
  ```
- Default interface methods can contain both implementation and abstract members.
- They improve flexibility in API design and reduce the need for helper classes or extension methods.
- Default interface methods help maintain backward compatibility and simplify interface versioning.

**64. What is the `lock` statement in C# and how is it used?**
- The `lock` statement is used to ensure that a block of code is executed by only one thread at a time.
- It helps prevent race conditions and ensures thread safety for shared resources.
- Example:
  ```csharp
  private static readonly object _lock = new object();
  
  public void SafeMethod() {
      lock (_lock) {
          // Critical section
      }
  }
  ```
- The `lock` statement acquires a mutual-exclusion lock on the specified object and releases it when the block is exited.
- It is commonly used for synchronizing access to shared data in multithreaded applications.
- Proper use of the `lock` statement helps avoid deadlocks and ensures data consistency.

**65. What is the purpose of `IDisposable` and how is it implemented?**
- The `IDisposable` interface provides a mechanism for releasing unmanaged resources.
- It defines a single method, `Dispose`, that is called to clean up resources.
- Example:
  ```csharp
  public class Resource : IDisposable {
      private bool _disposed = false;
      
      public void Dispose() {
          Dispose(true);
          GC.SuppressFinalize(this);
      }
      
      protected virtual void Dispose(bool disposing) {
          if (!_disposed) {
              if (disposing) {
                  // Dispose managed resources
              }
              // Dispose unmanaged resources
              _disposed = true;
          }
      }
      
      ~Resource() {
          Dispose(false);
      }
  }
  ```
- Implementing `IDisposable` ensures that resources such as file handles, database connections, and memory are properly released.
- The `using` statement can be used to automatically call `Dispose` when the object goes out of scope.
- Proper implementation of `IDisposable` helps prevent resource leaks and improves application stability.
