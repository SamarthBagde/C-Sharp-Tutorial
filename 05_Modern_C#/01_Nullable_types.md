# Nullable Types

`Nullable types` allow variables to represent the absence of a value (a null state).

C# divides nullability into two completely different mechanisms based on whether you are working with Value Types (like int, bool, struct) or Reference Types (like string, class)

## 1. Nullable Value Types

By default, value types cannot be `null` because they directly store data. A nullable value type allows these structures to hold either their standard range of values or an explicit `null` state.


```c#
int? age = null;
```

Now age can contain either any `int` value or `null`

```c#
//All are valid.

int? age = 25;

age = null;

age = 30;
```

### Underlying Type is Actually `Nullable<t>`

```c#
Nullable<int> age;

// shorthand 
int? age;
```

## 2. Nullable Reference Types

Reference types naturally contain a memory address pointer and have always been capable of being `null`.

Introduced in C# 8.0, Nullable Reference Types switch the compiler's default behavior from "anything can be null" to strict static safety tracking to mitigate runtime `NullReferenceException` occurrences.


`Enabling NRT`: Controlled at the project configuration level via the `<Nullable>enable</Nullable>` tag inside your .csproj file, or file-by-file with compiler directives.


```c#
#nullable enable

string nonNullableString = "Hello"; 
// nonNullableString = null; // Compiler Warning!

string? nullableString = null; // Perfect; explicitly allowed

// Compiler Warning: Dereference of a possibly null reference
Console.WriteLine(nullableString.Length); 

// Safe approach via static null-state analysis evaluation
if (nullableString != null)
{
    Console.WriteLine(nullableString.Length); // Allowed; compiler knows it isn't null here
}
```

## ?. — Null-Conditional Operator

`?.` means access this property/method only if the object isn't `null`.

```c#
string? name = null;

Console.WriteLine(name?.Length);
```

```
Is name null?
    ↓
   Yes
    ↓
Return null

Is name NOT null?
    ↓
   Yes
    ↓
Access Length
```

## ?? — Null-Coalescing Operator

`??` returns the value of its left-hand operand if it is not null; otherwise, it evaluates the right-hand operand and returns its result.

```c#
string? name = null;

string displayName = name ?? "Unknown";
```

Use `name` if it isn't `null`; otherwise use `"Unknown"`.

## ??= — Null-Coalescing Assignment

`??=` assign the value on the right only if the variable on the left is `null`.

```c#
string? name = null;

name ??= "Unknown";

/*
Since name is null:

name = "Unknown"
*/
```

#

| Syntax    | Meaning                      | Example               |
| --------- | ---------------------------- | --------------------- |
| `?`       | Allows null                  | `int? age`            |
| `?.`      | Safely access                | `user?.Name`          |
| `??`      | Use fallback if null         | `name ?? "Guest"`     |
| `??=`     | Assign fallback if null      | `name ??= "Guest"`    |
