### Set 21:

**121. What is an `ObservableCollection<T>` in C# and how is it used?**
- `ObservableCollection<T>` is a dynamic data collection that provides notifications when items get added, removed, or when the whole list is refreshed.
- It is part of the `System.Collections.ObjectModel` namespace and implements `INotifyCollectionChanged`.
- Example:
  ```csharp
  ObservableCollection<string> collection = new ObservableCollection<string>();
  collection.CollectionChanged += (sender, e) => {
      Console.WriteLine($"Action: {e.Action}");
  };
  collection.Add("Hello");
  collection.Remove("Hello");
  ```
- It is commonly used in data binding scenarios, especially with WPF and other UI frameworks.
- `ObservableCollection<T>` automatically updates the UI when the underlying data changes.
- Proper use of `ObservableCollection<T>` improves data-binding efficiency and synchronizes the UI with data changes.

**122. What is a `WeakEventManager` in C# and how is it used?**
- `WeakEventManager` allows events to be handled without creating strong references to the event source, preventing memory leaks.
- It is particularly useful in WPF for handling events in a memory-safe manner.
- Example:
  ```csharp
  public class Example {
      public event EventHandler MyEvent;

      public void RaiseEvent() {
          MyEvent?.Invoke(this, EventArgs.Empty);
      }
  }

  public class EventListener {
      public EventListener(Example example) {
          WeakEventManager<Example, EventArgs>.AddHandler(example, "MyEvent", Handler);
      }

      private void Handler(object sender, EventArgs e) {
          Console.WriteLine("Event handled");
      }
  }

  Example example = new Example();
  EventListener listener = new EventListener(example);
  example.RaiseEvent(); // Outputs "Event handled"
  ```
- `WeakEventManager` manages the event subscription and unsubscription process, ensuring no strong references are held.
- It is used to avoid memory leaks in event-driven applications, particularly in scenarios involving long-lived objects.
- Proper use of `WeakEventManager` enhances application performance and reliability by preventing memory leaks.

**123. What is the `using` statement in C# and how does it differ from the `using` directive?**
- The `using` statement is used to ensure that `IDisposable` objects are disposed of properly, releasing unmanaged resources.
- Example:
  ```csharp
  using (var stream = new FileStream("file.txt", FileMode.Open)) {
      // Use the stream
  } // stream is disposed here
  ```
- The `using` directive is used to include namespaces in a file, simplifying code by avoiding fully qualified names.
  ```csharp
  using System;
  using System.Collections.Generic;
  ```
- The `using` statement provides deterministic disposal of resources, while the `using` directive helps organize code and improve readability.
- Both constructs serve different purposes and enhance code maintainability and resource management.
- Proper use of the `using` statement and directive improves code clarity, resource handling, and prevents memory leaks.

**124. What is the difference between `FirstOrDefault` and `SingleOrDefault` in C#?**
- `FirstOrDefault` returns the first element of a sequence, or a default value if the sequence is empty.
  ```csharp
  var numbers = new List<int> { 1, 2, 3 };
  int first = numbers.FirstOrDefault(); // Outputs 1
  int firstEmpty = numbers.Where(n => n > 3).FirstOrDefault(); // Outputs 0 (default for int)
  ```
- `SingleOrDefault` returns the only element of a sequence, or a default value if the sequence is empty, but throws an exception if there is more than one element.
  ```csharp
  var numbers = new List<int> { 2 };
  int single = numbers.SingleOrDefault(); // Outputs 2
  int singleEmpty = numbers.Where(n => n > 2).SingleOrDefault(); // Outputs 0 (default for int)
  var multiple = new List<int> { 1, 2, 3 };
  int singleMultiple = multiple.SingleOrDefault(); // Throws InvalidOperationException
  ```
- `FirstOrDefault` is used when any element is acceptable, whereas `SingleOrDefault` ensures that only one specific element is present.
- Both methods return a default value if the sequence is empty, but `SingleOrDefault` enforces uniqueness.
- Proper use of these methods enhances query precision and ensures correct handling of sequences with varying element counts.

**125. What is the `yield` keyword in C# and how is it used?**
- The `yield` keyword is used in an iterator method to return each element of a collection one at a time.
- It simplifies the creation of custom iterators without the need for temporary collections.
- Example:
  ```csharp
  public IEnumerable<int> GetNumbers() {
      for (int i = 0; i < 5; i++) {
          yield return i;
      }
  }

  foreach (var number in GetNumbers()) {
      Console.WriteLine(number); // Outputs 0 1 2 3 4
  }
  ```
- `yield return` returns an element and pauses the method execution until the next element is requested.
- `yield break` ends the iteration.
  ```csharp
  public IEnumerable<int> GetEvenNumbers(int limit) {
      for (int i = 0; i < limit; i++) {
          if (i % 2 == 0) {
              yield return i;
          } else if (i > 10) {
              yield break;
          }
      }
  }
  ```
- The `yield` keyword enhances code readability and efficiency by eliminating the need for explicit state management.
- Proper use of `yield` simplifies the implementation of iterators and improves performance in iterative methods.

**126. What is the `dynamic` keyword in C# and how is it used?**
- The `dynamic` keyword allows for late binding, deferring type checking until runtime.
- It enables dynamic programming, where the type of the variable can change, and members are resolved at runtime.
- Example:
  ```csharp
  dynamic value = 10;
  Console.WriteLine(value.GetType()); // Outputs System.Int32

  value = "Hello";
  Console.WriteLine(value.GetType()); // Outputs System.String

  dynamic person = new ExpandoObject();
  person.Name = "John";
  Console.WriteLine(person.Name); // Outputs "John"
  ```
- `dynamic` is useful for scenarios involving COM interop, reflection, or working with dynamically typed objects.
- It provides flexibility but sacrifices compile-time type safety.
- Proper use of `dynamic` enhances code flexibility and interoperability, especially in scenarios requiring dynamic behavior.

**127. What is the difference between `XmlDocument` and `XDocument` in C#?**
- `XmlDocument` is part of the `System.Xml` namespace and represents an in-memory XML document using the DOM (Document Object Model) approach.
  ```csharp
  XmlDocument doc = new XmlDocument();
  doc.LoadXml("<root><element>value</element></root>");
  XmlNode node = doc.SelectSingleNode("/root/element");
  Console.WriteLine(node.InnerText); // Outputs "value"
  ```
- `XDocument` is part of the `System.Xml.Linq` namespace and represents an XML document using the LINQ to XML approach, providing a more modern and flexible API.
  ```csharp
  XDocument xDoc = XDocument.Parse("<root><element>value</element></root>");
  XElement element = xDoc.Descendants("element").FirstOrDefault();
  Console.WriteLine(element.Value); // Outputs "value"
  ```
- `XmlDocument` uses the traditional DOM API, while `XDocument` uses a LINQ-based API, making it more intuitive for LINQ users.
- `XDocument` offers better performance and easier manipulation of XML data compared to `XmlDocument`.
- Both classes are used for XML manipulation, but `XDocument` is preferred for new development due to its simplicity and efficiency.
- Proper use of `XmlDocument` and `XDocument` enhances XML processing capabilities and improves code readability.

**128. What is the `Parallel` class in C# and how is it used?**
- The `Parallel` class provides support for parallel loops and regions, enabling parallel execution of code.
- It is part of the `System.Threading.Tasks` namespace and includes methods like `Parallel.For` and `Parallel.ForEach`.
- Example:
  ```csharp
  Parallel.For(0, 10, i => {
      Console.WriteLine($"Processing {i}");
  });

  var numbers = Enumerable.Range(0, 10).ToList();
  Parallel.ForEach(numbers, number => {
      Console.WriteLine($"Processing {number}");
  });
  ```
- `Parallel` methods improve performance by utilizing multiple processors and threads for concurrent execution.
- They provide a simple way to parallelize iterative operations without manual thread management.
- Proper use of the `Parallel` class enhances application performance and scalability by leveraging parallelism.

**129. What is a `BackgroundWorker` in C# and how is it used?**
- `BackgroundWorker` is a class that simplifies the implementation of asynchronous operations with support for progress reporting and cancellation.
- It is part of the `System.ComponentModel` namespace and is often used for long-running tasks in Windows Forms applications.
- Example:
  ```csharp
  BackgroundWorker worker = new BackgroundWorker {
      WorkerReportsProgress = true,
      WorkerSupportsCancellation = true
  };

  worker.DoWork += (sender, e) => {
      for (int i = 0; i <= 100;

 i++) {
          if (worker.CancellationPending) {
              e.Cancel = true;
              break;
          }
          System.Threading.Thread.Sleep(50);
          worker.ReportProgress(i);
      }
  };

  worker.ProgressChanged += (sender, e) => {
      Console.WriteLine($"Progress: {e.ProgressPercentage}%");
  };

  worker.RunWorkerCompleted += (sender, e) => {
      if (e.Cancelled) {
          Console.WriteLine("Operation cancelled");
      } else {
          Console.WriteLine("Operation completed");
      }
  };

  worker.RunWorkerAsync();
  ```
- `BackgroundWorker` manages the execution and synchronization of background tasks, simplifying UI updates and task management.
- It provides events for reporting progress and handling task completion or cancellation.
- Proper use of `BackgroundWorker` enhances application responsiveness and user experience by offloading long-running tasks to the background.

**130. What is the `JsonConvert` class in C# and how is it used?**
- `JsonConvert` is a class in the `Newtonsoft.Json` library, used for converting objects to and from JSON format.
- It provides methods like `SerializeObject` and `DeserializeObject` for JSON serialization and deserialization.
- Example:
  ```csharp
  var person = new { Name = "John", Age = 30 };
  string json = JsonConvert.SerializeObject(person);
  Console.WriteLine(json); // Outputs {"Name":"John","Age":30}

  var deserializedPerson = JsonConvert.DeserializeObject<dynamic>(json);
  Console.WriteLine(deserializedPerson.Name); // Outputs "John"
  ```
- `JsonConvert` simplifies JSON processing in .NET applications, providing an easy-to-use API for working with JSON data.
- It supports advanced features like type handling, custom converters, and formatting options.
- Proper use of `JsonConvert` enhances data exchange, serialization, and deserialization in JSON-based applications.
