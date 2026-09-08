# Hashset

Hashset is an unordered collection of unique elements.

It is part of the `System.Collections.Generic` namespace

### Key Characteristics

- `No Duplicates`: Automatically prevents duplicate elements; attempting to add a duplicate returns false.

- `Unordered`: It does not maintain any insertion or sorting order.

- `No Indexing`: You cannot access elements using an index.

- `High Performance`: Provides average O(1) time complexity for addition, removal, and lookup operations.

```c#
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        // 1. Initialization
        HashSet<string> countries = new HashSet<string>();

        // 2. Adding Elements
        countries.Add("USA");
        countries.Add("Canada");
        countries.Add("UK");

        // Attempting to add a duplicate returns false and is ignored
        bool isAddedAgain = countries.Add("USA"); 
        Console.WriteLine($"Was USA added again? {isAddedAgain}"); // Output: False

        // 3. Checking Existence (Extremely Fast O(1))
        if (countries.Contains("Canada"))
        {
            Console.WriteLine("Canada is in the set.");
        }

        // 4. Removing Elements
        countries.Remove("UK");

        // 5. Iteration
        foreach (var country in countries)
        {
            Console.WriteLine(country); // Output order is not guaranteed
        }
    }
}
```

### Hashset methods

- Add() - adds an item to the HashSet.
    ```c#
    HashSet<int> numbers = new HashSet<int>();

    numbers.Add(101);
    numbers.Add(102);
    ```
- Contains() - Checks whether a value exists.
    ```c#
    if (numbers.Contains(101))
    {
        Console.WriteLine("101 id exists");
    }
    ```
- Remove() - Removes a specific value.
    ```c#
    numbers.Remove(102);
    ```
- Clear() - Removes all elements.
    ```c#
    numbers.Clear();
    ```
- Count - tells how many unique elements exist.
    ```c#
    Console.WriteLine(numbers.Count);
    ```
- UnionWith() - All unique elements from both sets.
    ```c#
    setA.UnionWith(setB);
    ```
- IntersectWith() - Elements that exist in both sets.
    ```c#
    setA.IntersectWith(setB);
    ```
- ExceptWith() - removes elements that also exist in another collection
    ```c#
    HashSet<int> setA = new HashSet<int>
    {
        1, 2, 3, 4
    };

    HashSet<int> setB = new HashSet<int>
    {
        3, 4, 5, 6
    };

    setA.ExceptWith(setB);

    // 1 2
    ```
- IsSubsetOf() - Checks whether all elements of one set exist in another
    ```c#
    HashSet<int> setA = new HashSet<int>
    {
        1, 2
    };

    HashSet<int> setB = new HashSet<int>
    {
        1, 2, 3, 4
    };

    Console.WriteLine(setA.IsSubsetOf(setB)); // true
    ```
- SetEquals() - Checks whether two sets contain exactly the same elements.
    ```c#
    HashSet<int> setA = new HashSet<int>
    {
        1, 2, 3
    };

    HashSet<int> setB = new HashSet<int>
    {
        3, 2, 1
    };

    Console.WriteLine(setA.SetEquals(setB)); // true
    ```