# Lambda expressions

A `lambda expression` is a short way of writing a function/method without explicitly declaring a method.

Syntax : 
```
(parameters) => expression
```

Ex : 
```c#
x => x * 2
```

Lambda expressions are heavily used with `delegates`, `LINQ`, `Action`, `Func`, and `Predicate`.

### Lambda with `Func`

```c#
Func<int, int> square = x => x * x;

/*
Func<int, int>
      ↓    ↓
    input output
*/
```

```c#
Func<int, int, int> add = (a, b) => a + b;
```
```c#
Action sayHello = () => Console.WriteLine("Hello");

Action<string> print = message =>
{
    Console.WriteLine(message);
};
```


### Lambda with `Predicate`

`Predicate<T>` represents a function that returns bool.

```c#
Predicate<int> isEven = x => x % 2 == 0;
```