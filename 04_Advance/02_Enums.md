# Enums

An `enum` (enumeration) is a special type in C# that allows you to define a set of named constant values.

By default, the underlying type of an `enum` is `int`, and the numbering starts at `0` and increments by `1` for each subsequent member.

```c#
enum Status
{
    Pending, // value : 0
    Active, // value : 1
    Completed, // value : 2
    Cancelled // value : 3
}

// Note : This values (0,1,2,3) are underlying enum type (int)

// Now we can use it:

Status status = Status.Active;
```

```c#
Console.WriteLine((int)status); // 1
```

### Assigning Custom Values

You can explicitly assign numbers.

```c#
enum Status
{
    Pending = 1,
    Active = 2,
    Completed = 3,
    Cancelled = 4
}
```

Enum Values Can Automatically Continue

If you specify one value, the following values continue from it.

```c#
enum Status
{
    Pending = 10,
    Active,
    Completed,
    Cancelled
}

/*
Pending    → 10
Active     → 11
Completed  → 12
Cancelled  → 13
*/
```

### Converting Integer to Enum

```c#
int value = 2;

Status status = (Status)value;

Console.WriteLine(status); // Active
```

## Flags enum

There is a special type of enum called a Flags enum. It is used when multiple values can be selected at the same time.

```c#
[Flags]
enum Permission
{
    None   = 0,
    Read   = 1,
    Write  = 2,
    Delete = 4
}
```
You can combine permissions using `|` :

```c#
Permission permission = Permission.Read | Permission.Write;
```
Now the user has: Read and Write


## Enum vs Constantss

Why not just use constants ?

enum groups related values into one meaningful type. This provides much better readability and type safety.

## Note : 

Enums are value types in C#. not reference types