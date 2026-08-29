# Constructors

Constructors is a special method within a class or struct that is automatically called when an object of that class is created.

Its primary purpose is to initialize the object's data members and set up a valid initial state.

### Key Characteristics

- `Same Name as class`: It must have the exact same name as the class it belongs to.

- `No Return Type`: It does not return any value, not even void.

- `Automatic Execution`: It is triggered automatically using the `new` keyword.

- `Overloading`: A class can have multiple constructors with different parameters.

```c#
class Player
{
    public string Name;
    public int Health;

    public Player(string name, int health) // Constructors
    {
        Name = name;
        Health = health;
    }
}
```


## Types of Constructors ( Total 5 types)

### 1. Default Constructor

Takes no arguments. 

If you do not write any constructor, the C# compiler provides a parameterless default constructor automatically to clear numeric fields to `0` and references to `null`.

```c#
public class Car 
{
    public string Model;
    public int number; // this get initialize with 0 automatically 

    // Default Constructor
    public Car() 
    {
        Model = "Unknown";
    }
}
```

### 2. Parameterized Constructor

Accepts arguments to initialize object properties with specific custom values at the time of creation.

```c#
public class Car 
{
    public string Model;
    public int Number;

    // Parameterized Constructor
    public Car(string modelName, int Number) 
    {
        Model = modelName;
        this.Number = Number
    }
}

// Usage:
Car myCar = new Car("Mustang", 01234);
```



### 3. Copy Constructor

Creates a new object by copying the values and data state from an existing object of the same class.

```c#
public class Car 
{
    public string Model;

    public Car(string modelName) { Model = modelName; }

    // Copy Constructor
    public Car(Car previousCar) 
    {
        Model = previousCar.Model;
    }
}
```


### 4. Private Constructor

Defined with a private access specifier. 

It prevents external code from creating instances of the class. 

This is highly useful in classes containing only static utilities or when implementing the Singleton design pattern.

```c#
public class DatabaseUtility 
{
    // Private Constructor
    private DatabaseUtility() { } 
    
    public static void Connect() { /* connection logic */ }
}
```

Note : Can't create object of this class

### 5. Static Constructor

Used to initialize static data members or perform a one-time class configuration.

It takes no access modifiers, has no parameters, and runs automatically exactly once before the first instance is created or any static member is referenced


```c#
public class Configuration
{
    public static string Environment;

    // Static Constructor
    static Configuration() 
    {
        Environment = "Production";
    }
}
```


## Note 

- Constructors cannot be marked as `virtual` or `abstract`
- If you write a parameterized constructor, `C#` stops providing the automatic parameterless default constructor.
- You can leverage Constructor Chaining using the `this` keyword to make one constructor invoke another constructor within the same class, minimizing code repetition.

    ```c#
    public class Employee
    {
        public string Name;
        public string Role;
        public int Salary;

        // 1. Main Constructor (Does the actual work)
        public Employee(string name, string role, int salary)
        {
            Name = name;
            Role = role;
            Salary = salary;
        }

        // 2. Chained Constructor (Passes a default salary of 40000)
        public Employee(string name, string role) : this(name, role, 40000)
        {
            // No extra code needed here
        }

        // 3. Chained Constructor (Passes a default role and salary)
        public Employee(string name) : this(name, "Intern", 25000)
        {
            // No extra code needed here
        }
    }

    // ------------------------------------------------------------
    
    // Calls Constructor 3 -> Chains to Constructor 1
    Employee emp1 = new Employee("Alice"); 
    // Result: Name = "Alice", Role = "Intern", Salary = 25000

    // Calls Constructor 2 -> Chains to Constructor 1
    Employee emp2 = new Employee("Bob", "Developer"); 
    // Result: Name = "Bob", Role = "Developer", Salary = 40000

    // Calls Constructor 1 directly
    Employee emp3 = new Employee("Charlie", "Manager", 80000); 
    // Result: Name = "Charlie", Role = "Manager", Salary = 80000
    ```