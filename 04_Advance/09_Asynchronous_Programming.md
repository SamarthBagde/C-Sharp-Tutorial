# Asynchronous Programming

Asynchronous programming allows your program to start a task that may take time and continue doing other work instead of waiting/blocking for that task to finish.

## Synchronous vs Asynchronous

**1. Synchronous** : Synchronous execution in C# means that code statement execution happens sequentially, one line after the other

When a method is called, the current executing thread halts and waits until that entire operation completes before it moves forward to the next task.

```c#
Console.WriteLine("Task 1");

Thread.Sleep(5000);

Console.WriteLine("Task 2");
```

The program does:
```
Task 1
  ↓
Wait 5 seconds
  ↓
Task 2
```
During those 5 seconds, the current thread is blocked.

This is `synchronous/blocking` behavior.


**2. Asynchronous** : Asynchronous programming in C# is a method of executing code without blocking the main application thread.

It allows your program to start a long-running operation (like a database query, file download, or API call) and continue doing other work while waiting for that operation to complete

```c#
Console.WriteLine("Start");

await Task.Delay(5000);

Console.WriteLine("Finished");
```

Conceptually:

```
Start
  ↓
Start async delay
  ↓
Thread can do other useful work
  ↓
5 seconds complete
  ↓
Finished
```

**`await` doesn't mean "block the thread for this duration." It means "pause this `async` method until the awaited operation completes, while allowing the thread to do other work."**

## The main keywords in Asynchronous Programming

### 1. async

`async` tells C# that a method contains asynchronous operations and can use `await`.

```c#
static async Task DoSomethingAsync()
{
    await Task.Delay(2000);

    Console.WriteLine("Done");
}
```

### 2. await

`await` is an operator that temporarily suspends the execution of an asynchronous method until the targeted task finishes

```c#
static async Task TestAsync()
{
    Console.WriteLine("Start");

    await Task.Delay(3000);

    Console.WriteLine("End");
}
```

### 3. Task

`Task` is an object that represents an asynchronous operation

```c#
Task task = Task.Delay(5000);
```

This means start an operation that completes after 5 seconds


- `Task`: Represents an operation that returns no value (similar to returning void).
- `Task<TResult>`: Represents an operation that returns a specific data type TResult


```c#
async Task SaveUserAsync()
{
    await Task.Delay(1000);
}
```
