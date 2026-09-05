# Static Keyword

The `static` keyword in C# means that something belongs to the class itself, rather than to a specific object of that class.

```
Normal member
    ↓
Belongs to an object

-------------------------------------------

static member
    ↓
Belongs to the class
```

### 1. Static Fields and Properties

Used to hold data that must be shared across all instances of a class. Only one copy exists in memory.

Common Use: Counters or global configuration settings.

```c#
ublic class User
{
    // Shared by all User objects
    public static int TotalUsers = 0; 
    
    public User()
    {
        TotalUsers++; // Increments the shared counter
    }
}
// Usage:
User u1 = new User();
User u2 = new User();
Console.WriteLine(User.TotalUsers); // Outputs: 2
```

### 2. Static Methods

Methods that perform actions but do not rely on data from a specific object.

Means that method belong to the class and we can call it directly with class name 

```c#
public static class Calculator
{
    public static int Add(int a, int b) => a + b;
}
// Usage: Called directly via class name
int sum = Calculator.Add(5, 10); 
```

Note : Static methods cannot access instance variables or use the `this` keyword. They can only access other static members.

### 3. Static Classes

A class declared as `static` acts strictly as a container for static members.

Rule :

- Cannot be instantiated using the new keyword.
- Cannot be inherited (sealed by default).
- Cannot implement interfaces.
- Must only contain static members.

```c#
static class Calculator
{
    public static int Add(int a, int b)
    {
        return a + b;
    }

    public static int Subtract(int a, int b)
    {
        return a - b;
    }
}
```

A `static` class is useful when you have functionality that doesn't need object-specific data.


### 4. Static Constructor

Used to initialize static data or perform a setup action that only needs to happen once.

It is called automatically by the runtime before the first instance is created or any static members are accessed. It cannot take parameters or access modifiers.

Static constructors are useful for initializing static resources.

```c#
class Database
{
    static Database()
    {
        Console.WriteLine("Database initialized");
    }

    public static void Connect()
    {
        Console.WriteLine("Connected");
    }
}

//---------------------------------

Database.Connect();
Database.Connect();

/*
Output :

Database initialized
Connected
Connected
*/
```


## Why Is Main() Static?

Because the program needs an entry point before you have created a Program object.

The runtime can call:

```c#
Program.Main();
```
without creating:
```c#
new Program();
```