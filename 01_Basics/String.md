# String in c#

`string` represents a sequential collection of read-only Unicode characters used to store and manipulate text

```c#
string name = "Samarth";

Console.WriteLine(name[0]);
Console.WriteLine(name[1]);
```

## String methods 

### 1. Length

```c#
string name = "Samarth";

Console.WriteLine(name.Length);

// 7
```

### 2. ToUpper()

```c#
string name = "Samarth";

Console.WriteLine(name.ToUpper());
```
### 3. ToLower()

```c#
Console.WriteLine(name.ToLower());
```

### 4. Contains()

```c#
string name = "Abcd efgh";

Console.WriteLine(name.Contains("efgh"));

// true
```

### 5. StartsWith() and EndsWith()

```c#
string name = "Abcd efgh";

Console.WriteLine(name.StartsWith("Abc"));

Console.WriteLine(name.EndsWith("gh"));

// true
```
### 6. Substring()

You can extract part of a string.

The method offers two overloads

- `Substring(int startIndex)` : Extracts text from the startIndex all the way to the end of the string.
- `Substring(int startIndex, int length)` : Extracts a specific number of characters (length) starting from the startIndex

```c#
using System;

class Program
{
    static void Main()
    {
        string message = "Hello, C# Programmer!";

        // 1. Extracting to the very end
        string part1 = message.Substring(7); 
        Console.WriteLine(part1); // Output: "C# Programmer!"

        // 2. Extracting a specific length
        string part2 = message.Substring(7, 2); 
        Console.WriteLine(part2); // Output: "C#"
    }
}
```

### 7. Replace()
substitutes all occurrences of a specified character or substring and returns a new string

```c#
string original = "Hello World";
// Replaces "World" with "C#"
string result = original.Replace("World", "C#"); 

Console.WriteLine(result); // Output: Hello C#
```

### 8. Trim()
```c#
string name = "   Samarth   ";

Console.WriteLine(name.Trim());

// Samarth
```