# Properties

`Property` is a class member that provides a flexible mechanism to read, write, or compute the value of a private field

```c#
class Player
{
    public string Name { get; set; }
    public int Health { get; set; }
}
```

# Getter and Setter

`getters` and `setters` are accessors used inside properties to control how the values of a class's private fields are read and modified

```c#
public int Health { get; set; }

player.Health = 100; // set
Console.WriteLine(player.Health); // get
```

get → read the value<br>
set → change the value

# Read-Only Property

You can prevent outside code from changing a property:

```c#
public string Name { get; private set; }
```

```c#
// Now inside the class 
Name = "Samarth"; // is allowed. ✅

// But outside:
player.Name = "Sam"; // is not allowed. ❌
```