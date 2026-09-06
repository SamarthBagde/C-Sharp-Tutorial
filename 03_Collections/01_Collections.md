# Collections

Collections in C# are specialized, resizable classes designed to store, manage, and manipulate groups of related data efficiently.

It used to store and manage multiple values/objects together

### Modern `.NET` organizes collections into four main namespaces based on type safety, performance, and concurrency requirements:

## 1. Generic Collections (System.Collections.Generic)

These are the standard, strongly typed collections preferred in modern C# development. 

They prevent type mismatches at compile time and eliminate the performance overhead of boxing and unboxing value types.

```c#
using System;
using System.Collections.Generic;

// Initialization using modern Collection Expressions
List<string> shoppingList = ["Apples", "Milk", "Bread"];
```

## 2. Non-Generic Collections (System.Collections)

Legacy classes that store items as a universal `System.Object` type.

They accept heterogeneous data but require explicit type casting and degrade performance due to boxing/unboxing.

```c#
using System;
using System.Collections;

// Can mix completely different data types in the same collection
ArrayList legacyData = new ArrayList();
legacyData.Add("Hello World");
legacyData.Add(42); 
legacyData.Add(true);
```

## 3. Concurrent Collections (System.Collections.Concurrent)

Thread-safe classes designed for multi-threaded applications. 

They safely manage data contention across multiple simultaneous threads without requiring manual synchronization or thread locks

```c#
using System;
using System.Collections.Concurrent;

ConcurrentDictionary<int, string> activeUsers = new ConcurrentDictionary<int, string>();

// Safe atomic operation: Adds the key-value pair if it doesn't exist, 
// or updates the existing value if the key already exists.
activeUsers.AddOrUpdate(101, "User_A", (key, oldValue) => "User_A_Updated");
```

## 4. Immutable Collections (System.Collections.Immutable)

Collections that cannot be altered after creation. 

Modifying an immutable collection (e.g., adding an item) returns an entirely new, mutated instance, leaving the original intact.

They offer inherent thread safety and prevent unintended side effects in complex systems.

```c#
using System;
using System.Collections.Immutable;

// Create an initial immutable list
ImmutableList<string> originalPlanets = ["Mercury", "Venus", "Earth"];

// Attempting to add an item returns a NEW instance
ImmutableList<string> updatedPlanets = originalPlanets.Add("Mars");

// The original list remains exactly as it was created
Console.WriteLine($"Original count: {originalPlanets.Count}"); // Output: 3
Console.WriteLine($"Updated count: {updatedPlanets.Count}");   // Output: 4
```



## Main Collection Types in C#

```
Collections
│
├── List<T>
│
├── Dictionary<TKey, TValue>
│
├── HashSet<T>
│
├── Queue<T>
│
├── Stack<T>
│
└── Other collections
```