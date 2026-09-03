# Polymorphism

`Polymorphism` is a fundamental pillar of Object-Oriented Programming (OOP) that translates from Greek to mean `"many forms"`

One thing can have many forms or behave differently depending on the situation.

### In C#, polymorphism mainly comes in two forms: 
`Compile-Time (Static)` and `Runtime (Dynamic)` polymorphism

```
Polymorphism
│
├── 1. Compile-time polymorphism
│      └── Method Overloading
│
└── 2. Runtime polymorphism
       └── Method Overriding
```


## 1. Compile-Time Polymorphism

Compile-time polymorphism means the compiler determines which method to call during compilation.

### a. Method Overloading: 
Creating multiple methods in the same class with the identical name but distinct parameter types or counts.

```c#
class Calculator
{
    public int Add(int a, int b)
    {
        return a + b;
    }

    public int Add(int a, int b, int c)
    {
        return a + b + c;
    }
}
```

Different Ways to Overload a Method

- Different number of parameters
    ```
    void Print(string name)
    {
    }

    void Print(string name, int age)
    {
    }
    ```
- Different parameter types
    ```
    void Print(int number)
    {
    }

    void Print(string text)
    {
    }
    ```
- Different order of parameter types
    ```
    void Display(int id, string name)
    {
    }

    void Display(string name, int id)
    {
    }
    ```

<b>Note</b>: Changing only the return type is not enough. 

### b. Operator Overloading: 
Customizing how standard operators (like +, -, *, ==, etc.) behave when applied to user-defined types or classes


[Click here to Know More About Operator Overloading](07.1_Operator_Overloading.md)


## 2. Runtime Polymorphism

Runtime polymorphism happens when the method that executes is determined at runtime, based on the actual object.

In runtime polymorphism, the decision of which method to execute is deferred until the application runs. 

The `Common Language Runtime (CLR)` evaluates the actual object type at execution, rather than relying on the declared reference variable type.

### a. Method Overriding:

A derived child class replaces or extends a method inherited from a parent base class

<b>Note</b>: 
- The base class must explicitly flag the method as `virtual` (or abstract) to permit overrides.
- The derived class must use the `override` keyword to supply its updated logic

```c#
class Animal // base class
{
    public virtual void MakeSound() // we marked this as virtual 
    {
        Console.WriteLine("Animal makes a sound");
    }
}

class Dog : Animal // derived class 1
{
    public override void MakeSound() // we marked this as override
    {
        Console.WriteLine("Dog barks");
    }
}

class Cat : Animal // derived class 1
{
    public override void MakeSound() // we marked this as override
    {
        Console.WriteLine("Cat meows");
    }
}

// -----------------------------------------

// This is inheritance + overriding.
Dog dog = new Dog();
Cat cat = new Cat();

dog.MakeSound(); // Dog barks
cat.MakeSound(); // Cat meows

// This is runtime polymorphism.
Animal animal1 = new Dog();
Animal animal2 = new Cat();

animal1.MakeSound(); // Dog barks
animal2.MakeSound(); // Cat meows
```

### Why Does This Work?

```
Animal animal1 = new Dog();
```

There are two different types involved:

```
Animal → reference type
Dog    → actual object
```

The variable is an Animal, but the actual object is a Dog.

When you call: `animal1.MakeSound();` <br>
C# looks at the actual object at runtime.

The actual object is `Dog` So it executes `Dog.MakeSound()`


## Method Overloading vs Method Overriding

| Feature               | Overloading  | Overriding                             |
| --------------------- | ------------ | -------------------------------------- |
| Polymorphism          | Compile-time | Runtime                                |
| Inheritance required? | ❌ No         | ✅ Yes                                  |
| Same method name      | ✅            | ✅                                      |
| Parameters            | Must differ  | Usually same                           |
| `virtual` required?   | ❌            | Base method generally virtual/abstract |
| `override` required?  | ❌            | ✅                                      |
| Decision              | Compile time | Runtime                                |
