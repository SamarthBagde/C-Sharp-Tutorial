# Dictionary

Dictionary is a generic collection from the `System.Collections.Generic` namespace that stores data in unique key-value pairs.

It provides `O(1)` time complexity for lookups, insertions, and deletions because it uses a hash table structure internally

```c#
using System.Collections.Generic;

// Method 1: Standard initialization
Dictionary<int, string> employees = new Dictionary<int, string>();

// Method 2: Initialization with a collection initializer
var capitals = new Dictionary<string, string>
{
    { "USA", "Washington, D.C." },
    { "UK", "London" }
};
```

To read data 

```c#
capitals["USA"];
```

You shouldn't always access a dictionary like, if the key might not exist.

Instead use this:

```c#
if (capitals.TryGetValue("USA", out String capital))
{
    Console.WriteLine(capital);
}
else
{
    Console.WriteLine("Contry not found");
}
```

### Dictionary Methods

- Add
  ```c#
  students.Add(104, "Rohit");
  ```
- Access using [ ]
  ```c#
  // retrieve a value using its key
  string name = students[101];

  //update a value
  students[101] = "Raj";
  ```
- ContainsKey() — Check if a key exists
  ```c#
  if (students.ContainsKey(102))
    {
        Console.WriteLine("Student exists");
    }
  ```
- ContainsValue() — Check if a value exists
  ```c#
  if (students.ContainsValue("Amit"))
    {
        Console.WriteLine("Amit exists");
    }
  ```
- Remove() — Remove by key
  ```c#
  students.Remove(102);
  ```
- Clear() — Remove everything
  ```c#
  students.Clear();
  ```

- Count — Number of items<br>
    `Count` is a property, not a method.
    ```c#
    Console.WriteLine(students.Count);
    ```
- Keys — Get all keys
    ```C#
    foreach (int key in students.Keys)
    {
        Console.WriteLine(key);
    }
    ```
- Values — Get all values
    ```C#
    foreach (string value in students.Values)
    {
        Console.WriteLine(value);
    }
    ```
 


### Iterate through key-value pairs

```c#
foreach (KeyValuePair<int, string> student in students)
{
    Console.WriteLine(
        $"ID: {student.Key}, Name: {student.Value}"
    );
}
```