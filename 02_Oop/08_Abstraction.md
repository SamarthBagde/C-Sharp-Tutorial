# Abstraction 

`Abstraction` means hiding unnecessary implementation details and exposing only the essential functionality.

In `C#`, you achieve abstraction using two main mechanisms: `Abstract Classes` and `Interfaces`.

## Abstract Classes

An abstract class is an incomplete class that cannot be instantiated directly.

It acts as a strict blueprint for derived classes and can contain a mix of both implemented code and unimplemented placeholders (abstract method)

### 1. Abstract Methods: 
Declared with the abstract keyword, they contain no body and must be overridden in derived classes.

### 2. Concrete Methods: 
Regular methods with a fully functional body that child classes inherit automatically.


```c#
using System;

// Abstract class providing the concept of a "Vehicle"
abstract class Vehicle 
{
    // Abstract method (No implementation details)
    public abstract void StartEngine();

    // Concrete method (Shared implementation)
    public void Honk() 
    {
        Console.WriteLine("Beep beep!");
    }
}

// Concrete derived class fulfilling the contract
class Car : Vehicle 
{
    // Providing the mandatory specific implementation
    public override void StartEngine() 
    {
        Console.WriteLine("Car engine started: Vroom!");
    }
}

class Program 
{
    static void Main() 
    {
        // Vehicle myVehicle = new Vehicle(); // Error: Cannot instantiate abstract class
        
        Car myCar = new Car();
        myCar.StartEngine(); // Output: Car engine started: Vroom!
        myCar.Honk();        // Output: Beep beep!
    }
}
```


### Why Do We Need Abstract Classes?

Suppose we have:

```
Animal
├── Dog
├── Cat
└── Cow
```
All animals make sounds, but the sound is different.

```c#
abstract class Animal
{
    public abstract void MakeSound();
}
```

Every Animal must have a MakeSound() method, but the specific implementation depends on the derived class.

### Note 

- You Cannot Create an Object of an Abstract Class
- Abstract Class Can Have Normal Methods
- Abstract Class Can Have Fields
- Abstract Class Can Have Constructors

    - we can't able to create object even if abstract class have constructore because the class contains a non implemented abstarct method

    ```c#
    abstract class Animal
    {
        protected string Name;

        protected Animal(string name)
        {
            Name = name;
        }

        public abstract void MakeSound();
    }

    class Dog : Animal
    {
        public Dog(string name)
            : base(name)
        {
        }

        public override void MakeSound()
        {
            Console.WriteLine($"{Name} says Bark");
        }
    }
    ```

### Abstract Properties

we can also have abstract properties.

```c#
abstract class Animal
{
    public abstract string Sound { get; }
}

class Dog : Animal
{
    public override string Sound
    {
        get
        {
            return "Bark";
        }
    }
}
```