# LINQ

`LINQ` stands for Language Integrated Query.

It allows you to query, filter, sort, transform, group, and aggregate data using `C#` syntax.

```c#
List<int> numbers = new List<int>
{
    1, 2, 3, 4, 5, 6
};

var evenNumbers = numbers
    .Where(x => x % 2 == 0)
    .ToList();
```

## 1. Where()

`Where()` is used to filter data.

```c#
List<int> numbers = new List<int>
{
    10, 15, 20, 25, 30
};

var result = numbers
    .Where(x => x > 20)
    .ToList();

/*
25, 30
*/
```

## 2. Select()

`Select()` is used to transform data.

```c#
List<int> numbers = new List<int>
{
    1, 2, 3, 4, 5
};

var result = numbers
    .Select(x => x * 2)
    .ToList();

// 2, 4, 6, 8, 10
```

## 3. OrderBy()

Used to sort data in ascending order.

```c#
var result = students
    .OrderBy(s => s.Age)
    .ToList();
```

## 4. OrderByDescending()

Sort in descending order

```c#
var result = students
    .OrderByDescending(s => s.Age)
    .ToList();
```

## 5. ThenBy()

Perform a secondary sort on a collection in ascending order

```c#
var result = students
    .OrderBy(s => s.Age)
    .ThenBy(s => s.Name)
    .ToList();
```

## 6. First()

Gets the first element.

```c#
var student = students.First();
```

## 7. FirstOrDefault()

Safely retrieve the first element in a collection, or a default value if no matching element is found

```c#
var student = students
    .FirstOrDefault(s => s.Name == "John");

// If John doesn't exist, it returns: null
```

Returns the default value of the type (null for reference types, 0 for int, false for bool).

## 8. Single() and SingleOrDefault()

Used to retrieve exactly one element from a collection


```c#
var student = students
    .Single(s => s.Id == 1);
```

If there are:
- zero matches → exception
- more than one match → exception
- exactly one match → returns it

`SingleOrDefault()` :

```c#
var student = students
    .SingleOrDefault(s => s.Id == 1);
```

## 9. Any()

Checks whether at least one element satisfies a condition.

```c#
bool exists = students
    .Any(s => s.Age > 24);

// return true or false
```

### Other methods

- All() ->Checks whether every element satisfies a condition.
- Count() -> Counts elements
- Sum() -> Calculate the total.
- Average()
- Min() and Max()
- Distinct() -> Remove duplicates
- Contains()
- Skip() -> Skip certain number of elements 
- Take() -> Take a certain number of elements.
- GroupBy() -> Used to group data.
- ToList() -> to convert `IEnumerable<T>` to List. 

Many LINQ operations return an `IEnumerable<T>` rather than a `List<T>`.

##
| Method                | Purpose               |
| --------------------- | --------------------- |
| `Where()`             | Filter                |
| `Select()`            | Transform             |
| `OrderBy()`           | Sort ascending        |
| `OrderByDescending()` | Sort descending       |
| `ThenBy()`            | Secondary sorting     |
| `First()`             | First item            |
| `FirstOrDefault()`    | First item or default |
| `Single()`            | Exactly one item      |
| `SingleOrDefault()`   | Zero or one item      |
| `Any()`               | Check if any exists   |
| `All()`               | Check if all match    |
| `Count()`             | Count items           |
| `Sum()`               | Calculate total       |
| `Average()`           | Calculate average     |
| `Min()`               | Minimum               |
| `Max()`               | Maximum               |
| `Distinct()`          | Remove duplicates     |
| `Contains()`          | Check for value       |
| `Skip()`              | Skip items            |
| `Take()`              | Take items            |
| `GroupBy()`           | Group items           |
| `ToList()`            | Convert to list       |
