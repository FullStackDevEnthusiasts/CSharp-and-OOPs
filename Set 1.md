### Set 1:

**1. What are the four main principles of Object-Oriented Programming?**
- Encapsulation: Bundling the data (variables) and the code (methods) that manipulates the data into a single unit or class. Example: A `Car` class with properties like `speed` and methods like `Accelerate()`.
- Abstraction: Hiding complex implementation details and showing only the necessary features of an object. Example: A `TV` class might have a method `TurnOn()`, but the internal workings of how the TV turns on are hidden.
- Inheritance: The process where one class (child class) inherits properties and behavior (methods) from another class (parent class). Example: A `Dog` class inheriting from an `Animal` class.
- Polymorphism: The ability to present the same interface for different underlying forms (data types). Example: A base class `Shape` with a method `Draw()` that is implemented differently in derived classes `Circle` and `Square`.

**2. What is the difference between an abstract class and an interface in C#?**
- Abstract class can have implementations for some of its members (methods), but an interface cannot.
- A class can inherit only one abstract class but can implement multiple interfaces.
- Abstract class members can have access modifiers, but interface members are always public.
- Abstract class can define fields, but an interface cannot.
- Example: An abstract class `Vehicle` with an implemented method `Start()` and an interface `IDrivable` with a method `Drive()`.

**3. What is method overloading and method overriding?**
- Method overloading allows multiple methods in the same class to have the same name but different parameters.
- Method overriding allows a derived class to provide a specific implementation of a method that is already defined in its base class.
- Overloading is resolved at compile time, while overriding is resolved at runtime.
- Example of overloading: `public void Print(int i)` and `public void Print(string s)`.
- Example of overriding: A base class `Animal` with a method `Speak()`, and a derived class `Dog` overriding `Speak()` with its own implementation.

**4. What is a constructor and what are its types in C#?**
- A constructor is a special method of a class that initializes objects of that class.
- Types of constructors include: Default constructor, Parameterized constructor, Copy constructor, Static constructor, and Private constructor.
- Default constructor does not take any parameters.
- Parameterized constructor takes parameters to initialize the object with specific values.
- Static constructor is used to initialize static members of the class.
- Example: `public class Car { public Car() { } public Car(string model) { } }`

**5. What is the difference between a class and an object in C#?**
- A class is a blueprint or template that defines the properties and behaviors of objects.
- An object is an instance of a class.
- Class is declared using the `class` keyword, while an object is created using the `new` keyword.
- Example: `class Car { }` is a class declaration, while `Car myCar = new Car();` is the creation of an object.
- Class can have fields, methods, constructors, properties, etc.
- Objects use the class structure to store data and execute functions.
