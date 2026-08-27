# 1.  Variables in C#

A variable is a named location used to store a value.

Ex. : int age = 22;


# 2. Data Types

```
C# Data Types
│
├── Value Types
│   ├── Integral
│   │   ├── sbyte // signed byte
│   │   ├── byte  // unsigned byte (+ve value only )
│   │   ├── short
│   │   ├── ushort
│   │   ├── int
│   │   ├── uint
│   │   ├── long
│   │   └── ulong
│   │
│   ├── Floating Point
│   │   ├── float
│   │   └── double
│   │
│   ├── decimal 
│   ├── char // Stores one Unicode character.
│   ├── bool
│   ├── enum
│   ├── struct
│   └── nullable value types
│
└── Reference Types
    ├── string
    ├── object
    ├── class
    ├── interface
    ├── array
    ├── delegate
    └── record

```

Note : 
<br> Value type → stores the actual value.<br> 
Reference type → stores a reference to an object.


## a. Integral Types

These store whole numbers.

| Type     |   Size | Range                        |
| -------- | -----: | ---------------------------- |
| `sbyte`  |  8-bit | -128 to 127                  |
| `byte`   |  8-bit | 0 to 255                     |
| `short`  | 16-bit | -32,768 to 32,767            |
| `ushort` | 16-bit | 0 to 65,535                  |
| `int`    | 32-bit | -2.1B to 2.1B                |
| `uint`   | 32-bit | 0 to 4.2B                    |
| `long`   | 64-bit | Very large negative/positive |
| `ulong`  | 64-bit | Very large positive          |


## b. Floating-Point Types

Floating-Point Types
There are two main types: float and double

- float is 32-bit floating-point number.


    - Ex.:  float height = 5.10f;

    - Notice: `5.10f`. The `f` tells C# that the value is a float.

- double is 64-bit floating-point number.

    - Ex. : double height = 5.10;
    - double is generally the default choice for general-purpose decimal calculations.


## c. decimal

decimal is designed for high-precision decimal calculations.

Ex.:  decimal price = 999.99m;

### Note : 
- `double` is a fast, 64-bit binary floating-point type used for scientific calculations where speed matters more than absolute precision, 
- while `decimal` is a highly precise, 128-bit decimal floating-point type specifically designed for financial calculations where rounding errors are unacceptable 

## d. object

`object` is the base type of all C# types.

You can store different types in an object variable:

Ex.:
```c#
object value = 10; 
value = "Hello";
value = 10.5;
value = true;
```

## e. dynamic

`dynamic` tells C# to resolve the type at runtime rather than compile time.

Ex.: 
```c#
dynamic value = 10;

value = "Hello";

value = true;
```

## f. delegate

A `delegate` represents a reference to a method.

`delegate` is a type-safe function pointer that holds a reference to a method with a specific parameter list and return type

## g. record

`record` is a reference type designed primarily for storing data.

a specialized type (either a class or a struct) designed primarily to encapsulate data rather than behavior

## h. Nullable Value Types

Normally:

```c# 
int age = 22;
```

cannot contain null.<br>
But you can make it nullable:

```c#
int? age = null;
```
Now it can contain: any number or null

```c#
int? age = null;

age = 22;
```


## i. Special Pointer Types
C# also supports pointer types in unsafe code:

```c# 
unsafe
{
    int number = 10;
    int* pointer = &number;
}
```
These are used for low-level/native programming.