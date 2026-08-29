# Class

A class is a blueprint/template for creating objects.

```c#
class Player
{
    public string Name;
    public int Health;
    public float Speed;

    public void Move()
    {
        Console.WriteLine("Player is moving");
    }

    public void Attack()
    {
        Console.WriteLine("Player is attacking");
    }
}
```
This class is just a blueprint.

It doesn't represent a particular player yet.


### A class normally contains two major things: `Data` and `Behavior`

```
Class
│
├── Data
│   ├── Name
│   ├── Health
│   └── Speed
│
└── Behavior
    ├── Move()
    └── Attack()
```


# Object

An object is an actual instance of a class.

We create an object using `new` keyword.

```c#
Player player1 = new Player();
```
Now we can give the player data:

```c#
player1.Name = "Samarth";
player1.Health = 100;
player1.Speed = 5.5f;
```

Call its methods:

```c#
player1.Move();
player1.Attack();
```

# `this` Keyword

`this` refers to the current object.

```c#
class Player
{
    public string Name;

    public void SetName(string Name)
    {
        this.Name = Name;
    }
}

// this.Name belonging to object
// 'Name' is method parameter
```

