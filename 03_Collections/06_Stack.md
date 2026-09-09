# Stack 

The `Stack` class in the `System.Collections.Generic` namespace is a collection that follows the Last-In, First-Out (LIFO) principle. 

The item that is added last is removed first.

```c#
Stack<string> pages = new Stack<string>();
```

### Stack Methods

- Push() - add an item to the top of the stack.
    ```c#
    Stack<string> pages = new Stack<string>();
    pages.Push("Home");
    ```
- Pop() - removes and returns the item from the top.
    ```c#
    string page = pages.Pop();
    ```
- Peek() - returns the top item without removing it.
    ```c#
    string page = pages.Peek();
    ```
- Count - tells how many items are currently in the stack<br>Count is a property, not a method.
    ```c#
    Console.WriteLine(pages.Count);
    ```
- Contains() - Checks whether an item exists.
    ```c#
    if (pages.Contains("Home"))
    {
        Console.WriteLine("Home exists");
    }
    ```
- Clear() - Removes everything from the stack.
    ```c#
    pages.Clear();
    ```
- TryPop() - If the stack might be empty, using Pop() can cause an exception
    ```c#
    if (pages.TryPop(out string page))
    {
        Console.WriteLine($"Removed: {page}");
    }
    else
    {
        Console.WriteLine("Stack is empty");
    }
    ```
- TryPeek() - safely checks the top item
    ```c#
    if (pages.TryPeek(out string page))
    {
        Console.WriteLine($"Top page: {page}");
    }
    else
    {
        Console.WriteLine("Stack is empty");
    }
    ```