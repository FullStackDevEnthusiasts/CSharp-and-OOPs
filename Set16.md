### Set 16:

**76. What is the difference between `StringBuilder` and `string` in C#?**
- `string` is immutable, meaning any modification creates a new string instance.
  ```csharp
  string str = "Hello";
  str += " World"; // Creates a new string instance
  ```
- `StringBuilder` is mutable and optimized for scenarios where repeated modifications are needed.
  ```csharp
  StringBuilder sb = new StringBuilder("Hello");
  sb.Append(" World"); // Modifies the existing instance
  ```
- `StringBuilder` is more efficient for large or numerous string manipulations due to its ability to modify the same instance.
- `string` is preferred for scenarios with minimal or no modifications.
- Using `StringBuilder` reduces memory overhead and improves performance for complex string operations.

**77. What is the purpose of the `nameof` operator in C#?**
- The `nameof` operator returns the string name of a variable, type, or member.
- Example:
  ```csharp
  public class Example {
      public int Property { get; set; }
  }

  string propertyName = nameof(Example.Property);
  Console.WriteLine(propertyName); // Outputs "Property"
  ```
- It is used for refactoring-safe code, providing a way to reference names without hardcoding strings.
- `nameof` improves code readability and maintainability, especially in logging, exceptions, and data binding.
- It helps avoid errors caused by manually typed string names and ensures that name changes are automatically updated.

**78. What is dependency injection and how is it implemented in C#?**
- Dependency injection (DI) is a design pattern for achieving Inversion of Control (IoC) between classes and their dependencies.
- It allows for the injection of dependencies, typically via constructor, property, or method injection.
- Example with constructor injection:
  ```csharp
  public interface IService {
      void Serve();
  }

  public class Service : IService {
      public void Serve() {
          Console.WriteLine("Service Called");
      }
  }

  public class Client {
      private readonly IService _service;

      public Client(IService service) {
          _service = service;
      }

      public void Start() {
          _service.Serve();
      }
  }

  // Usage with DI container (e.g., Microsoft.Extensions.DependencyInjection)
  var serviceProvider = new ServiceCollection()
      .AddSingleton<IService, Service>()
      .AddSingleton<Client>()
      .BuildServiceProvider();

  var client = serviceProvider.GetService<Client>();
  client.Start();
  ```
- DI promotes loose coupling and enhances testability by allowing dependencies to be injected rather than hardcoded.
- It is commonly implemented using DI containers, which manage the lifetime and resolution of dependencies.
- DI improves code flexibility and scalability by centralizing dependency management.

**79. What is the difference between `throw` and `throw ex` in exception handling?**
- `throw` rethrows the current exception while preserving the original stack trace.
  ```csharp
  try {
      // Code that may throw an exception
  } catch (Exception ex) {
      // Handle exception
      throw; // Rethrows the original exception
  }
  ```
- `throw ex` throws a new exception with the current exception as the inner exception, which resets the stack trace.
  ```csharp
  try {
      // Code that may throw an exception
  } catch (Exception ex) {
      // Handle exception
      throw ex; // Throws a new exception
  }
  ```
- Preserving the stack trace is important for debugging and understanding the original source of the error.
- Using `throw ex` should be avoided unless there is a specific need to modify the exception or add additional context.
- Properly rethrowing exceptions helps maintain the integrity of exception handling and debugging.

**80. What is the purpose of the `await` keyword in C# and how is it used?**
- The `await` keyword is used to asynchronously wait for a `Task` to complete.
- It pauses the execution of the method until the awaited `Task` is completed, then resumes execution.
- Example:
  ```csharp
  public async Task ExampleAsync() {
      await Task.Delay(1000); // Simulate async work
      Console.WriteLine("Task completed");
  }

  public async Task MainAsync() {
      await ExampleAsync();
      Console.WriteLine("Main completed");
  }
  ```
- The `await` keyword can only be used within methods marked with the `async` modifier.
- It simplifies asynchronous programming by allowing asynchronous operations to be written in a synchronous style.
- Using `await` improves responsiveness and scalability by allowing non-blocking operations.
