# Inheritance

Inheritance is a fundamental Object-Oriented Programming (OOP) concept that allows a new class (derived/child class) to reuse, modify, and extend the data and behavior of an existing class (base/parent class)

It allows a class to acquire properties and methods from another class and extend or modify them.

```c#
// parent class
class Animal
{
    public void Eat()
    {
        Console.WriteLine("Animal is eating");
    }
}

// child class
class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Dog is barking");
    }
}


Dog dog = new Dog();

dog.Eat(); // Animal is eating  
dog.Bark(); // Dog is barking
```

## Types of Inheritance

C# directly supports the following inheritance forms:

### 1. Single Inheritance

One class derives from one base class

```c#
class Animal
{
    public void Eat()
    {
        Console.WriteLine("Eating");
    }
}

class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Barking");
    }
}
```

### 2. Multilevel Inheritance

Multilevel inheritance means inheritance happens across multiple levels.

Class A serves as a base class for the derived class B, which serves as a base class for the derived class C.

```c#
class Animal
{
    public void Eat()
    {
        Console.WriteLine("Eating");
    }
}

class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Barking");
    }
}

class Puppy : Dog
{
    public void Play()
    {
        Console.WriteLine("Playing");
    }
}
```

### 3. Hierarchical Inheritance

Multiple classes derive from a single base class.

```
        Animal
       /    \
      ↓      ↓
    Dog      Cat
```

```c#
class Animal
{
    public void Eat()
    {
        Console.WriteLine("Eating");
    }
}

class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Barking");
    }
}

class Cat : Animal
{
    public void Meow()
    {
        Console.WriteLine("Meowing");
    }
}
```

### 4. Multiple Inheritance (Through Interfaces)

Multiple inheritance means: One class inherits from multiple classes.

Note : `C#` doesn't allow this with classes.

Why Doesn't C# Allow Multiple Class Inheritance?

- One major problem is the diamond problem.
    ```
       A
      / \
     B   C
      \ /
       D
    ```
- Suppose A has: Display()
- Both B and C inherit from A. Then D inherits from both B and C.
- Now which version should D use if both B and C define Display()? This creates ambiguity.
- `C#` avoids this problem by not allowing multiple inheritance between classes.


Using `interfaces` we can achive `Multiple Inheritance`

```c#
interface IWalkable
{
    void Walk();
}

interface ISwimmable
{
    void Swim();
}

// Multiple Inheritance
class Human : IWalkable, ISwimmable
{
    public void Walk()
    {
        Console.WriteLine("Walking");
    }

    public void Swim()
    {
        Console.WriteLine("Swimming");
    }
}
```


### 5. Hybrid Inheritance

Hybrid inheritance is a combination of multiple inheritance types.

```
           Animal
           /    \
          Dog    Cat
           |
         Puppy
```

This combines:

Hierarchical inheritance<br>
Multilevel inheritance

However, because `C#` doesn't support `multiple inheritance` between classes, some `hybrid inheritance` structures aren't possible directly with classes.

`Interfaces` can be used to create more complex combinations.


## 

| Type                | Structure        | C#                                      |
| ------------------- | ---------------- | --------------------------------------- |
| Single              | `A → B`          | ✅                                       |
| Multilevel          | `A → B → C`      | ✅                                       |
| Hierarchical        | `A → B`, `A → C` | ✅                                       |
| Multiple classes    | `A + B → C`      | ❌                                       |
| Multiple interfaces | `IA + IB → C`    | ✅                                       |
| Hybrid              | Combination      | ✅ using suitable class/interface design |
