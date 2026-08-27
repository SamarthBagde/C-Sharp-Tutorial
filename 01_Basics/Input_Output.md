# 1. Output

### WriteLine()
prints something and moves to the next line.

```c#
Console.WriteLine("Hello");
Console.WriteLine("World");

// Hello
// World
```


### Write()
It doesn't move to the next line.
```c#
Console.Write("Hello ");
Console.Write("World");

// Hello World
```


# 2. Input

To get input from the user

```Console.ReadLine();```

```c#
Console.Write("Enter your name: ");

string name = Console.ReadLine();

Console.WriteLine($"Hello {name}");
```


### Note : Console.ReadLine() returns a string.


So if you want an integer, decimal :
```c#
Console.Write("Enter your age: ");

int age = Convert.ToInt32(Console.ReadLine());

double price = Convert.ToDouble(Console.ReadLine());
```