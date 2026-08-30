# Access Modifiers

Access modifiers control who can access something.

### 1. public

Accessible from anywhere.

```c#
public int power;
```

### 2. private

Accessible only inside the class.

```c#
private int power;
```

### 3. protected

Accessible inside the class and derived classes.

```c#
protected int power;
```

### 4. internal

Accessible within the same assembly/project.

`Same Assembly`: Any class or method in the same project can fully access internal items.


```c#
internal class Player
{
}
```