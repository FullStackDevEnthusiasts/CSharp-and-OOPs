### Set 7:

**31. What is method overriding in C#?**
- Method overriding allows a derived class to provide a specific implementation of a method already defined in its base class.
- The method in the base class must be marked as `virtual`, `abstract`, or `override`.
- The derived class uses the `override` keyword to define its version of the method.
- Example:
  ```csharp
  class BaseClass {
      public virtual void Display() {
          Console.WriteLine("Base Display");
      }
  }
  class DerivedClass : BaseClass {
      public override void Display() {
          Console.WriteLine("Derived Display");
      }
  }
  ```
- Overriding allows polymorphic behavior, enabling the correct method to be called based on the runtime type of the object.
- It helps in implementing runtime polymorphism and allows the derived class to extend or modify the base class behavior.

**32. What are properties in C# and how are they different from fields?**
- Properties are members that provide a flexible mechanism to read, write, or compute the values of private fields.
- They use `get` and `set` accessors to encapsulate the access to fields.
- Example:
  ```csharp
  class Person {
      private string name;
      public string Name {
          get { return name; }
          set { name = value; }
      }
  }
  ```
- Fields are variables declared directly in a class or struct.
- Properties provide controlled access to the fields, allowing validation, logging, or other operations to be performed when the value is accessed or modified.
- Properties improve encapsulation and are a key feature of the C# language for data access.

**33. What is the difference between `abstract` and `virtual` methods in C#?**
- `abstract` methods have no implementation in the base class and must be overridden in derived classes.
- `virtual` methods have an implementation in the base class but can be overridden in derived classes.
- `abstract` methods force derived classes to provide their own implementation, promoting a consistent interface.
- Example of an abstract method:
  ```csharp
  abstract class Animal {
      public abstract void MakeSound();
  }
  ```
- Example of a virtual method:
  ```csharp
  class Animal {
      public virtual void MakeSound() {
          Console.WriteLine("Animal Sound");
      }
  }
  ```
- `abstract` classes cannot be instantiated directly and are intended to be base classes, whereas `virtual` methods provide a base implementation that can optionally be overridden.

**34. What is the purpose of the `static` keyword in C#?**
- The `static` keyword indicates that a member belongs to the type itself rather than to a specific instance of the type.
- `static` members are shared among all instances of a class.
- `static` can be used with classes, methods, fields, properties, constructors, and events.
- Example:
  ```csharp
  class MathUtility {
      public static double Pi = 3.14;
      public static double Add(double a, double b) {
          return a + b;
      }
  }
  ```
- Static classes cannot be instantiated and can only contain static members.
- Static members are accessed using the class name, e.g., `MathUtility.Add(2, 3);`

**35. What are indexers in C# and how are they implemented?**
- Indexers allow objects to be indexed in a similar way to arrays.
- They provide a way to access elements in a class or struct using array-like syntax.
- Example:
  ```csharp
  class SampleCollection<T> {
      private T[] arr = new T[100];
      public T this[int i] {
          get { return arr[i]; }
          set { arr[i] = value; }
      }
  }
  ```
- Indexers use the `this` keyword followed by a parameter list in square brackets.
- They allow for defining custom behavior for element access, making classes more intuitive to use.
- Indexers can be overloaded to take multiple parameters, enhancing flexibility.

