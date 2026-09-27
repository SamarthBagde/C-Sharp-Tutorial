# Boxing

`Boxing` in `C#` is the process of implicitly converting a value type (like `int`, `char`, or a `struct`) into a reference type (`object` or an ``interface ``)

Ex:
```c#
int number = 10;

object obj = number;   // Boxing

/*
int value
   10
    │
    │ Boxing
    ▼
 object
 ┌──────┐
 │  10  │
 └──────┘
*/
```

C# cannot simply change the int variable into an object.

Instead, the runtime:

1. Allocates an object on the managed heap.
2. Copies the value `10` into that object.
3. Stores a reference to that object in `obj`.

```
Before boxing:

Stack
┌─────────────┐
│ number = 10 │
└─────────────┘


After boxing:

Stack                         Heap
┌─────────────┐              ┌─────────────┐
│ number = 10 │              │    10       │
└─────────────┘              │ boxed int   │
                             └─────────────┘
                                    ▲
                                    │
                              obj ──┘
```

So boxing creates a new object containing a copy of the value.

<hr>

# Unboxing

In C#, unboxing is the explicit process of converting a `reference type` (specifically a boxed `object` or `interface` type) back into its `original value type`.

Ex:

```c#
object obj = 100;

int number = (int)obj;

/*
object
  │
  │ Unboxing
  ▼
 int
 100
*/
```

Note : You need to explicitly tell `C#`, that "I know this object contains an int; give me that int."