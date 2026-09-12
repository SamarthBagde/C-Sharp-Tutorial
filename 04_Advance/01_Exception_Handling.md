# Exception
An exception is an unexpected event/error that occurs during program execution.

Ex:

```c#
int number = int.Parse("abc");
```

This causes `FormatException`


```
Exception
   │
   ├── DivideByZeroException
   ├── FormatException
   ├── NullReferenceException
   ├── IndexOutOfRangeException
   ├── InvalidOperationException
   └── ...
```

#  Exception Handling

`Exception handling` is used to handle errors that occur while program is running, so that your application doesn't unexpectedly crash.

Ex:

```c#
int a = 10;
int b = 0;

int result = a / b;
```
This cause `System.DivideByZeroException`

Without exception handling, the program can terminate. With exception handling, we can handle the problem gracefully.

`Exception handling` in `C#` is a structured mechanism using `try`, `catch`, `finally`, and `throw` blocks to manage runtime errors without crashing your application


## 1. try-catch

The most basic exception handling mechanism is `try-catch`

- `try`: Encloses the risky code that might cause a runtime error.
- `catch`: Intercepts and processes specific exceptions when they occur.


```c#
try
{
    // Code that might cause exception
}
catch
{
    // Handle exception
}
```


Example :

```c#
try
{
    int a = 10;
    int b = 0;

    int result = a / b;
}
catch (Exception ex)
{
    Console.WriteLine("Something went wrong");
    Console.WriteLine(ex.Message);
}
```

Note : We can have multiple `catch` blocks for different exceptions.

```c#
try
{
    int number = int.Parse("abc");
}
catch (FormatException)
{
    Console.WriteLine("Invalid number format.");
}
catch (OverflowException)
{
    Console.WriteLine("Number is too large.");
}
catch (Exception)
{
    Console.WriteLine("Some other error occurred.");
}
```

### Important Properties of Exception :

- Message : Contains a description of the error. (ex.Message)
- StackTrace : Shows where the exception occurred. (ex.StackTrace)
- InnerException : Sometimes one exception is caused by another exception. (ex.InnerException)


## 2. Finally block

`finally` contains code that should execute whether an exception occurs or not.

```c#
try
{
    // Code
}
catch
{
    // Handle exception
}
finally
{
    // Always executes
}
```

<b>Why Do We Need finally?</b>

A common use is resource cleanup.
```
Open file
   ↓
Read file
   ↓
Something goes wrong
   ↓
Close file
```

`finally` can be used for cleanup.

```c#
FileStream file = null;

try
{
    file = File.OpenRead("data.txt");

    // Work with file
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
finally
{
    file?.Close();
}
```

## 3. throw Keyword

Explicitly raises an `exception` manually to flag invalid logic

Sometimes we want to manually throw an exception. So we can use `throw` keyword

```c#
int age = 15;

if (age < 18)
{
    throw new Exception("User must be 18 or older.");
}
```

### Re-throwing an Exception

Suppose we catch an exception but want to pass it to another layer.

use 
```c#
catch (Exception ex)
{
    Console.WriteLine("Logging error...");

    throw;
}
```

`throw;` preserves the original stack trace.

`throw ex;` can reset the stack-trace information, making debugging harder.

# Custom Exceptions

We can create your own exception class.

```c#
class InsufficientBalanceException : Exception
{
    public InsufficientBalanceException(string message)
        : base(message)
    {
    }
}
```