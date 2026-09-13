# Delegates

A `delegate` is a type that can hold a reference to a method.

A `delegate` allows you to treat a method like a variable and pass that method around.

`delegate is a type-safe function pointer`

### Syntax

```c#
delegate returnType DelegateName(parameters);
```

Ex :


```c#
 delegate int Operation(int a, int b);
```

This delegate says: I can reference any method that accepts `two int values` and `returns an int`.


```c#
using System;

class Program
{
    delegate void Message();

    static void SayHello()
    {
        Console.WriteLine("Hello");
    }

    static void SayBye()
    {
        Console.WriteLine("Bye");
    }

    static void Main()
    {
        Message message = SayHello;

        message();

        message = SayBye;

        message();
    }
}
```


## Passing a Delegate to a Method

```c#
delegate int Operation(int a, int b);

//--------------------------------------

static int Calculate(
    int a,
    int b,
    Operation operation)
{
    return operation(a, b);
}

//--------------------------------------

static int Add(int a, int b)
{
    return a + b;
}

static int Multiply(int a, int b)
{
    return a * b;
}

//--------------------------------------

int result = Calculate(10, 5, Add);

Console.WriteLine(result); // 15

result = Calculate(10, 5, Multiply);

Console.WriteLine(result); // 50
```

## Multicast Delegates

A delegate can contain references to multiple methods.

`+=` -> to add<br>
`-=` -> to remove

```c#
delegate void Notification();

//--------------------------------

static void SendEmail()
{
    Console.WriteLine("Email sent");
}

static void SendSMS()
{
    Console.WriteLine("SMS sent");
}

//--------------------------------

Notification notification = SendEmail;

notification += SendSMS; 

//--------------------------------

notification(); 
/*
Email sent
SMS sent
*/
```


## Built-in Delegates

C# provides three very important built-in delegate types:

### 1. Action

`Action` represents a method that returns `void`.

```c#
Action sayHello = () =>
{
    Console.WriteLine("Hello");
};

sayHello(); // Hello
```
```c#
// Action<T>
Action<int> printNumber = number =>
{
    Console.WriteLine(number);
};

printNumber(100); // 100
```


### 2. Func

`Func` represents a method that returns something.

`Func<T, TResult>`

```c#
Func<int, int> square = x => x * x;

Console.WriteLine(square(5)); // 25

/*
Input  → int
Output → int
*/
```

### 3. Predicate

`Predicate<T>` returns bool.

```c#
Predicate<int> isEven = x => x % 2 == 0;

Console.WriteLine(isEven(10)); //true
```