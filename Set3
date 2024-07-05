### Set 3:

**11. What is polymorphism in C# and how is it implemented?**
- Polymorphism allows methods to do different things based on the object it is acting upon.
- Implemented through method overriding and method overloading.
- Method overriding allows a derived class to provide a specific implementation of a method already defined in its base class using the `override` keyword.
- Example: 
  ```csharp
  class Animal {
      public virtual void Speak() {
          Console.WriteLine("Animal speaks");
      }
  }
  class Dog : Animal {
      public override void Speak() {
          Console.WriteLine("Dog barks");
      }
  }
  ```
- Method overloading allows multiple methods with the same name but different signatures in the same class.
- Example: `public void Print(string s) { } public void Print(int i) { }`

**12. What is the use of the `base` keyword in C#?**
- `base` keyword is used to access members of the base class from within a derived class.
- It can be used to call a method, property, or constructor from the base class.
- Example: Calling the base class constructor:
  ```csharp
  class Animal {
      public Animal() {
          Console.WriteLine("Animal created");
      }
  }
  class Dog : Animal {
      public Dog() : base() {
          Console.WriteLine("Dog created");
      }
  }
  ```
- It helps to reuse the functionality of the base class in the derived class.
- It is often used in method overriding to call the base class method.

**13. Explain the concept of interfaces in C#.**
- An interface defines a contract that implementing classes must follow.
- Interfaces can contain declarations for methods, properties, events, and indexers but no implementations.
- A class or struct that implements an interface must provide implementations for all its members.
- Example:
  ```csharp
  interface IDrivable {
      void Drive();
  }
  class Car : IDrivable {
      public void Drive() {
          Console.WriteLine("Car is driving");
      }
  }
  ```
- Interfaces support multiple inheritance, allowing a class to implement multiple interfaces.
- They provide a way to achieve abstraction and loose coupling in code.

**14. What is the difference between `==` and `.Equals()` in C#?**
- `==` is an operator used for reference equality for reference types and value equality for value types.
- `.Equals()` is a method used for value equality and can be overridden in user-defined types.
- For reference types, `==` checks if two references point to the same object, while `.Equals()` can be overridden to compare object contents.
- Example:
  ```csharp
  string a = "hello";
  string b = "hello";
  bool isEqualUsingOperator = (a == b); // true
  bool isEqualUsingEqualsMethod = a.Equals(b); // true
  ```
- For value types, both `==` and `.Equals()` compare the values.
- Overriding `.Equals()` allows for custom comparison logic in user-defined types.

**15. What are access modifiers in C# and what are their types?**
- Access modifiers control the visibility and accessibility of classes, methods, and other members.
- Types of access modifiers:
  - `public`: Accessible from any code.
  - `private`: Accessible only within the containing class or struct.
  - `protected`: Accessible within the containing class and derived classes.
  - `internal`: Accessible within the same assembly but not from another assembly.
  - `protected internal`: Accessible within the same assembly or from derived classes.
- Example:
  ```csharp
  public class Car {
      private int speed;
      protected void Accelerate() { }
      internal void Start() { }
  }
  ```
- Proper use of access modifiers is essential for encapsulation and protecting the integrity of an object.
