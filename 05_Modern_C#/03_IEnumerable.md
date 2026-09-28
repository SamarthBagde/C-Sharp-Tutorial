# IEnumerable

`IEnumerable<T>` represents a sequence of elements that you can iterate through, usually using foreach.

It enables forward-only, read-only iteration over a collection of items.

If a `class` implements IEnumerable, it means you can use it inside a foreach loop.

```c#
IEnumerable<int> numbers = new List<int>
{
    10, 20, 30, 40
};

foreach (int number in numbers)
{
    Console.WriteLine(number);
}
```


# IAsyncEnumerable<T>