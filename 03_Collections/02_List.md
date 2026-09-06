# List

`List<T>` is a strongly typed, dynamically resizable collection of objects that can be accessed by an index.

It belongs to the `System.Collections.Generic` namespace and serves as a more flexible, modern alternative to a standard array

### Key Features

- `Dynamic Resizing`: Unlike fixed-size arrays, lists grow or shrink automatically as you add or remove elements.
- `Type Safety`: The generic parameter `<T>` forces the list to only accept a specified data type.
- `Permissive Storage`: It allows duplicate values and accepts null for reference types


```c#
List<int> numbers = new List<int>();

numbers.Add(10);
numbers.Add(20);
numbers.Add(30);
```

### List Methods

- Add
    ```c#
    numbers.Add(10);
    ```
- AddRange
    ```c#
    numbers.AddRange(new[] { 20, 30, 40 });
    ```
- Remove
    ```c#
    numbers.Remove(20); // Removes the first matching value.
    ```
- RemoveAt
    ```c#
    numbers.RemoveAt(0); // remove item at index
    ```
- Contains
    ```c#
    bool exists = numbers.Contains(21); // trun true if 21 exists
    ```
- Count
    ```c#
    Console.WriteLine(numbers.Count); // Returns the number of elements.
    ```
- Clear
    ```c#
    numbers.Clear(); // Removes everything.
    ```


### Looping Through a List

```c#
List<int> customerIds = new List<int>{1,2,3,4,5};

foreach(int id in customerIds){
    Console.WriteLine(id);
}
```