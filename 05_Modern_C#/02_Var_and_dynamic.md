# var

`var` is a C# keyword that lets the compiler automatically determine the type of a variable from the value you assign to it.

`var` does NOT mean the variable has no type. C# still gives it a specific, fixed type at compile time.

```c#
var age = 22;
```

C# looks at `22` and determines age → `int`


## `var` Is Strongly Typed

```c#
var age = 22; // int

age = "Samarth"; // ❌
```

because age is already an `int`.


# dynamic

`dynamic` used to bypass compile-time type checking, instructing the compiler to defer type resolution and member binding entirely to runtime.


```c#
dynamic value = 10;

value = "Hello"; // ✅
```
`dynamic` allows the type to be resolved at runtime.



#
```
var
 ↓
Type determined at compile time

dynamic
 ↓
Type resolved at runtime
```