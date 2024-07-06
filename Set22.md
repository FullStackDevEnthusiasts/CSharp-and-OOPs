### Set 22:

**131. What is `Expression Trees` in C# and how are they used?**
- Expression trees represent code in a tree-like data structure, where each node is an expression.
- They are part of the `System.Linq.Expressions` namespace and enable dynamic modification and execution of code.
- Example:
  ```csharp
  Expression<Func<int, int, int>> expression = (a, b) => a + b;
  var compiledExpression = expression.Compile();
  Console.WriteLine(compiledExpression(2, 3)); // Outputs 5
  ```
- Expression trees are used in LINQ providers, dynamic queries, and scenarios requiring runtime code manipulation.
- They allow for the inspection, modification, and execution of lambda expressions as data structures.
- Proper use of expression trees enhances flexibility and dynamic capabilities in code execution and query generation.

**132. What is a `ThreadStatic` attribute in C# and how is it used?**
- The `ThreadStatic` attribute marks a field as unique to the current thread.
- Each thread that accesses the field gets its own separate copy of the field.
- Example:
  ```csharp
  public class Example {
      [ThreadStatic] public static int threadSpecificField;

      public void SetField(int value) {
          threadSpecificField = value;
      }

      public int GetField() {
          return threadSpecificField;
      }
  }

  Example example = new Example();
  example.SetField(10);
  Console.WriteLine(example.GetField()); // Outputs 10
  ```
- It is used for scenarios where thread-specific data is required, ensuring thread isolation.
- Proper use of `ThreadStatic` enhances thread safety and data integrity in multi-threaded applications.
- It is important to initialize the field correctly for each thread, as the initial value is not set across all threads.

**133. What is the `MemoryCache` class in C# and how is it used?**
- `MemoryCache` provides a cache mechanism for storing objects in memory to improve application performance.
- It is part of the `System.Runtime.Caching` namespace and allows for efficient caching and retrieval of data.
- Example:
  ```csharp
  MemoryCache cache = MemoryCache.Default;
  string cacheKey = "myKey";
  cache.Set(cacheKey, "cachedValue", new CacheItemPolicy {
      AbsoluteExpiration = DateTimeOffset.Now.AddMinutes(10)
  });

  string cachedValue = cache.Get(cacheKey) as string;
  Console.WriteLine(cachedValue); // Outputs "cachedValue"
  ```
- `MemoryCache` supports cache policies, including absolute and sliding expirations, and cache item priorities.
- It improves performance by reducing redundant data retrieval and computation, leveraging in-memory storage.
- Proper use of `MemoryCache` enhances application efficiency, scalability, and response times.

**134. What is the `Regex` class in C# and how is it used?**
- The `Regex` class provides a way to work with regular expressions for pattern matching and text manipulation.
- It is part of the `System.Text.RegularExpressions` namespace and supports various regex operations.
- Example:
  ```csharp
  string input = "Hello, World!";
  string pattern = @"\w+";
  Regex regex = new Regex(pattern);

  MatchCollection matches = regex.Matches(input);
  foreach (Match match in matches) {
      Console.WriteLine(match.Value); // Outputs "Hello" and "World"
  }
  ```
- `Regex` supports pattern matching, replacement, and splitting operations on strings.
- It enables complex text processing and validation using regular expressions.
- Proper use of `Regex` enhances string manipulation capabilities, allowing for efficient and concise pattern matching.

**135. What is a `Semaphore` in C# and how is it used?**
- A `Semaphore` controls access to a resource by allowing a limited number of threads to enter a critical section.
- It is part of the `System.Threading` namespace and helps manage concurrent access to resources.
- Example:
  ```csharp
  Semaphore semaphore = new Semaphore(2, 2);

  for (int i = 0; i < 5; i++) {
      int workerId = i;
      Task.Run(() => {
          semaphore.WaitOne();
          Console.WriteLine($"Worker {workerId} entered critical section");
          Thread.Sleep(1000);
          Console.WriteLine($"Worker {workerId} leaving critical section");
          semaphore.Release();
      });
  }
  ```
- `Semaphore` supports controlling the number of concurrent threads accessing a resource, preventing overuse.
- It is used for managing limited resources, such as database connections or file handles.
- Proper use of `Semaphore` enhances resource management and prevents contention in multi-threaded applications.

**136. What is the `Monitor` class in C# and how is it used?**
- The `Monitor` class provides a mechanism for synchronizing access to objects, ensuring thread safety.
- It is part of the `System.Threading` namespace and supports lock acquisition and release.
- Example:
  ```csharp
  object lockObject = new object();

  void CriticalSection() {
      Monitor.Enter(lockObject);
      try {
          // Critical section
          Console.WriteLine("In critical section");
      } finally {
          Monitor.Exit(lockObject);
      }
  }
  ```
- `Monitor` supports methods like `Enter`, `Exit`, `Wait`, and `Pulse` for synchronization and signaling.
- It ensures mutual exclusion, preventing concurrent access to critical sections.
- Proper use of `Monitor` enhances thread safety and data integrity in concurrent applications.

**137. What is the `StreamWriter` class in C# and how is it used?**
- `StreamWriter` provides a way to write characters to a stream, such as a file or memory stream.
- It is part of the `System.IO` namespace and supports writing text data to streams.
- Example:
  ```csharp
  using (StreamWriter writer = new StreamWriter("file.txt")) {
      writer.WriteLine("Hello, World!");
  }
  ```
- `StreamWriter` supports methods for writing strings, characters, and formatted text to streams.
- It is commonly used for file I/O operations, including creating and updating text files.
- Proper use of `StreamWriter` enhances file handling and data persistence capabilities in applications.

**138. What is the `StringBuilder` class in C# and how is it used?**
- `StringBuilder` provides a mutable string representation, allowing for efficient modifications without creating new string instances.
- It is part of the `System.Text` namespace and supports dynamic string manipulation.
- Example:
  ```csharp
  StringBuilder sb = new StringBuilder();
  sb.Append("Hello");
  sb.Append(", ");
  sb.Append("World!");
  Console.WriteLine(sb.ToString()); // Outputs "Hello, World!"
  ```
- `StringBuilder` supports methods like `Append`, `Insert`, `Remove`, and `Replace` for dynamic string operations.
- It is more efficient than string concatenation for frequent modifications due to reduced memory allocation and copying.
- Proper use of `StringBuilder` enhances performance and memory management in scenarios involving extensive string manipulation.

**139. What is the `Lazy<T>` class in C# and how is it used?**
- `Lazy<T>` provides support for lazy initialization, deferring the creation of an object until it is needed.
- It is part of the `System` namespace and enhances performance by avoiding unnecessary object creation.
- Example:
  ```csharp
  Lazy<int> lazyValue = new Lazy<int>(() => {
      Console.WriteLine("Value created");
      return 42;
  });

  Console.WriteLine(lazyValue.IsValueCreated); // Outputs False
  Console.WriteLine(lazyValue.Value); // Outputs "Value created" and then 42
  Console.WriteLine(lazyValue.IsValueCreated); // Outputs True
  ```
- `Lazy<T>` supports thread-safe and non-thread-safe lazy initialization, configurable via its constructors.
- It is used for scenarios where resource-intensive objects should be created on-demand.
- Proper use of `Lazy<T>` enhances performance and resource management by deferring object creation until necessary.

**140. What is the `ConcurrentDictionary` class in C# and how is it used?**
- `ConcurrentDictionary` is a thread-safe dictionary implementation for concurrent read and write operations.
- It is part of the `System.Collections.Concurrent` namespace and supports high-performance concurrent access.
- Example:
  ```csharp
  ConcurrentDictionary<int, string> dictionary = new ConcurrentDictionary<int, string>();
  dictionary[1] = "Value1";

  string value;
  bool added = dictionary.TryAdd(2, "Value2");
  bool updated = dictionary.TryUpdate(1, "NewValue1", "Value1");
  bool removed = dictionary.TryRemove(2, out value);
  Console.WriteLine(added); // Outputs True
  Console.WriteLine(updated); // Outputs True
  Console.WriteLine(removed); // Outputs True and "Value2"
  ```
- `ConcurrentDictionary` supports atomic operations like `TryAdd`, `TryUpdate`, and `TryRemove` for thread-safe modifications.
- It is used in scenarios requiring efficient, concurrent access to dictionary data, such as in multi-threaded applications.
- Proper use of `ConcurrentDictionary` enhances performance, scalability, and thread safety in concurrent data access scenarios.
