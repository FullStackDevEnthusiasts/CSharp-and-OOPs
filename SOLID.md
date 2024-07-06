The SOLID principles are a set of design principles in object-oriented programming that aim to make software designs more understandable, flexible, and maintainable. These principles were introduced by Robert C. Martin, also known as Uncle Bob. SOLID is an acronym that stands for:

1. **S**ingle Responsibility Principle (SRP)
2. **O**pen/Closed Principle (OCP)
3. **L**iskov Substitution Principle (LSP)
4. **I**nterface Segregation Principle (ISP)
5. **D**ependency Inversion Principle (DIP)

Let's go through each principle with a C# example.

### 1. Single Responsibility Principle (SRP)
**Definition**: A class should have only one reason to change, meaning it should have only one job or responsibility.

**Example**:
```csharp
// Violation of SRP
public class Employee
{
    public string Name { get; set; }
    public string Position { get; set; }
    
    public void CalculatePay() 
    {
        // Calculate employee pay
    }
    
    public void GenerateReport() 
    {
        // Generate employee report
    }
}

// Adhering to SRP
public class Employee
{
    public string Name { get; set; }
    public string Position { get; set; }
}

public class PayCalculator
{
    public void CalculatePay(Employee employee) 
    {
        // Calculate employee pay
    }
}

public class ReportGenerator
{
    public void GenerateReport(Employee employee) 
    {
        // Generate employee report
    }
}
```

### 2. Open/Closed Principle (OCP)
**Definition**: Software entities (classes, modules, functions, etc.) should be open for extension but closed for modification.

**Example**:
```csharp
// Violation of OCP
public class Rectangle
{
    public double Width { get; set; }
    public double Height { get; set; }
}

public class AreaCalculator
{
    public double CalculateArea(Rectangle rectangle) 
    {
        return rectangle.Width * rectangle.Height;
    }
}

// Adhering to OCP
public abstract class Shape
{
    public abstract double CalculateArea();
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double CalculateArea() 
    {
        return Width * Height;
    }
}

public class Circle : Shape
{
    public double Radius { get; set; }

    public override double CalculateArea() 
    {
        return Math.PI * Radius * Radius;
    }
}

public class AreaCalculator
{
    public double CalculateArea(Shape shape) 
    {
        return shape.CalculateArea();
    }
}
```

### 3. Liskov Substitution Principle (LSP)
**Definition**: Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.

**Example**:
```csharp
// Violation of LSP
public class Bird
{
    public virtual void Fly() 
    {
        // Fly
    }
}

public class Ostrich : Bird
{
    public override void Fly() 
    {
        throw new NotImplementedException(); // Ostrich cannot fly
    }
}

// Adhering to LSP
public abstract class Bird
{
    // Other bird-related methods
}

public abstract class FlyingBird : Bird
{
    public abstract void Fly();
}

public class Sparrow : FlyingBird
{
    public override void Fly() 
    {
        // Fly
    }
}

public class Ostrich : Bird
{
    // Ostrich-specific methods
}
```

### 4. Interface Segregation Principle (ISP)
**Definition**: A client should not be forced to depend on methods it does not use. Instead of one large interface, multiple smaller, specific interfaces are preferred.

**Example**:
```csharp
// Violation of ISP
public interface IWorker
{
    void Work();
    void Eat();
}

public class Worker : IWorker
{
    public void Work() 
    {
        // Work
    }

    public void Eat() 
    {
        // Eat
    }
}

public class Robot : IWorker
{
    public void Work() 
    {
        // Work
    }

    public void Eat() 
    {
        throw new NotImplementedException(); // Robot doesn't eat
    }
}

// Adhering to ISP
public interface IWorkable
{
    void Work();
}

public interface IFeedable
{
    void Eat();
}

public class Worker : IWorkable, IFeedable
{
    public void Work() 
    {
        // Work
    }

    public void Eat() 
    {
        // Eat
    }
}

public class Robot : IWorkable
{
    public void Work() 
    {
        // Work
    }
}
```

### 5. Dependency Inversion Principle (DIP)
**Definition**: High-level modules should not depend on low-level modules. Both should depend on abstractions. Abstractions should not depend on details. Details should depend on abstractions.

**Example**:
```csharp
// Violation of DIP
public class LightBulb
{
    public void TurnOn() 
    {
        // Turn on the light
    }

    public void TurnOff() 
    {
        // Turn off the light
    }
}

public class Switch
{
    private LightBulb _lightBulb = new LightBulb();

    public void Operate() 
    {
        // Toggle light bulb
        _lightBulb.TurnOn();
    }
}

// Adhering to DIP
public interface ILight
{
    void TurnOn();
    void TurnOff();
}

public class LightBulb : ILight
{
    public void TurnOn() 
    {
        // Turn on the light
    }

    public void TurnOff() 
    {
        // Turn off the light
    }
}

public class Switch
{
    private readonly ILight _light;

    public Switch(ILight light) 
    {
        _light = light;
    }

    public void Operate() 
    {
        // Toggle light
        _light.TurnOn();
    }
}
```

These principles help in creating a robust and maintainable codebase. By following the SOLID principles, developers can ensure that their code is more adaptable to change and easier to understand.
