
### Set 4:

**16. What is the purpose of the `sealed` keyword in C#?**
- The `sealed` keyword prevents a class from being inherited.
- It can also be used to prevent method overriding in derived classes.
- Example of sealed class:
  ```csharp
  public sealed class SealedClass {
      // Members of the class
  }
  ```
- Example of sealed method:
  ```csharp
  public class BaseClass {
      public virtual void Display() { }
  }
  public class DerivedClass : BaseClass {
      public sealed override void Display() { }
  }
  ```
- Sealing a class or method can improve performance by enabling certain compiler optimizations.
- It ensures that the class or method implementation remains unchanged by subclasses.

**17. What are delegates in C# and how are they used?**
- A delegate is a type that represents references to methods with a specific parameter list and return type.
- Delegates are used to pass methods as arguments to other methods.
- They are similar to function pointers in C++ but are type-safe and secure.
- Example:
  ```csharp
  public delegate void Notify();
  public class Process {
      public event Notify ProcessCompleted;
      public void StartProcess() {
          // Process logic
          OnProcessCompleted();
      }
      protected virtual void OnProcessCompleted() {
          ProcessCompleted?.Invoke();
      }
  }
  ```
- Delegates are used extensively in event handling and callback mechanisms.
- They allow for defining and calling methods dynamically at runtime.

**18. What are events in C# and how do they work?**
- Events are a way for a class to notify other classes or objects when something of interest happens.
- An event is a special kind of delegate that can only be invoked from within the class where it is declared.
- Example:
  ```csharp
  public delegate void Notify();
  public class Process {
      public event Notify ProcessCompleted;
      public void StartProcess() {
          // Process logic
          OnProcessCompleted();
      }
      protected virtual void OnProcessCompleted() {
          ProcessCompleted?.Invoke();
      }
  }
  public class Program {
      public static void Main() {
          Process process = new Process();
          process.ProcessCompleted += Process_ProcessCompleted;
          process.StartProcess();
      }
      private static void Process_ProcessCompleted() {
          Console.WriteLine("Process Completed");
      }
  }
  ```
- Events follow the publish-subscribe pattern, where publishers raise events and subscribers handle them.
- They are used to provide a way for objects to communicate without tight coupling.

**19. What is the difference between abstract classes and concrete classes in C#?**
- Abstract classes cannot be instantiated directly and are intended to be base classes for other classes.
- Concrete classes can be instantiated and are fully implemented.
- Abstract classes can contain abstract methods (without implementation) and non-abstract methods (with implementation).
- Example of abstract class:
  ```csharp
  public abstract class Animal {
      public abstract void MakeSound();
      public void Sleep() {
          Console.WriteLine("Sleeping");
      }
  }
  ```
- Example of concrete class:
  ```csharp
  public class Dog : Animal {
      public override void MakeSound() {
          Console.WriteLine("Bark");
      }
  }
  ```
- Abstract classes are used to define a common interface for derived classes while allowing for some implementation reuse.

**20. What is the `object` class in C# and why is it important?**
- `object` is the base class for all types in C#.
- Every type in C# (value type or reference type) implicitly or explicitly derives from `object`.
- Important methods in the `object` class include `ToString()`, `Equals()`, `GetHashCode()`, and `GetType()`.
- Example:
  ```csharp
  object obj = new object();
  Console.WriteLine(obj.ToString());
  ```
- `ToString()` provides a string representation of the object.
- `Equals()` determines whether two object instances are equal.
- `GetHashCode()` returns a hash code for the object.
- `GetType()` gets the type of the current instance.

Would you like the next set?
