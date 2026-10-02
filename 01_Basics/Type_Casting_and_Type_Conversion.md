# Type Casting and Type Conversion

In C#, type casting and type conversion refer to the process of changing a value from one data type into another.

## 1. Implicit Conversion (Type Conversion)

Implicit conversions are handled automatically by the C# compiler.

They happen when you move a value from a smaller data type to a larger data type, or from a derived class to a base class.

These operations are completely safe and guarantee zero data loss.

```c#
int myInt = 42;
// Automatically converts 32-bit int to 64-bit double
double myDouble = myInt; 

Console.WriteLine(myDouble); // Output: 42
```

## 2. Explicit Conversion (Type Casting)

Explicit conversions require manual intervention via a cast operator—the target type wrapped in parentheses `(type)`. 

This is necessary when converting a larger type to a smaller type (narrowing conversion) or a base class back to a derived class

Note: Explicit casting can cause `data loss` (such as dropping decimal precision) or trigger an `InvalidCastException` if types are incompatible.

```c#
double myDouble = 9.78;
// Manually trunctuates the fractional part to fit into an integer
int myInt = (int)myDouble; 

Console.WriteLine(myInt); // Output: 9
```

# Conversion via Helper Classes & Methods

When types are completely fundamentally incompatible (such as converting a `string` text into an `int`), direct casting will fail. `C#` provides built-in tools for these scenarios :

- `Parse()` and `TryParse()`: 

    Used to convert `string` representations into `numeric` or `boolean` types. `TryParse()` is highly recommended because it returns a boolean instead of crashing your program if the conversion fails.

- `System.Convert` Class:  

    Provides extensive methods like ToInt32(), ToDouble(), and ToString() to safely translate across common framework types.


```c#
string ageInput = "25";

// Using Parse
int age = int.Parse(ageInput); 

// Using TryParse (Safer approach)
bool isValid = int.TryParse(ageInput, out int result);

// Using Convert class
bool isTrue = Convert.ToBoolean(1); // Output: True
```