# Value Type

`Value type` is a data type that directly stores its data values within its own allocated memory space.

```c#
using System;

class Program
{
    static void Main()
    {
        int a = 10;   // 'a' directly stores the value 10 on the stack
        int b = a;    // 'b' copies the value from 'a'. A new '10' is created.

        b = 20;       // Modifying 'b' does NOT affect 'a'

        Console.WriteLine($"a: {a}"); // Output: a: 10
        Console.WriteLine($"b: {b}"); // Output: b: 20
    }
}
```

Common value types include : 
```
int
float
double
decimal
bool
char
byte
short
long
struct
enum
```


# Reference Type

`Reference type` is a data type that stores the memory address (reference) of its data, rather than storing the actual data directly.

The actual data is allocated on a managed memory area called the `heap`, while the variable holding the pointer/address typically sits on the stack.

```c#
using System;

class Person 
{
    public string Name { get; set; }
}

class Program 
{
    static void Main() 
    {
        // Allocates memory on the heap for a Person object
        Person p1 = new Person { Name = "Alice" }; 
        
        // Copies the memory address reference from person1 to person2
        Person p2 = p1; 
        
        // Modifying person2 changes the underlying object data on the heap
        p2.Name = "Bob"; 
        
        // Both point to the same data, so both output "Bob"
        Console.WriteLine(p1.Name); // Output: Bob
        Console.WriteLine(p2.Name); // Output: Bob
    }
}
```

```
Stack                  Heap
┌──────────────┐       ┌──────────────┐
│ p1 ──────────┼──────→│ Person       │
│ p2 ──────────┼──────→│ Name=Bob     │
└──────────────┘       └──────────────┘
```

Reference types :

```
class
interface
delegate
object
string
arrays
```

## 
**Value type stores the actual value.<br>
Reference type stores a reference to an object.**