# Queue 

A Queue is a collection that follows the FIFO (First In, First Out) principle.

```c#
Queue<int> customerIds = new Queue<int>();
```
or 
```c#
// initialize directly
Queue<int> customerIds = new Queue<int>
{
    101,
    102,
    102,
    104
};
```


### Queue Methods

- aEnqueue() — Add an Item
    ```c#
    Queue<string> orderQueue = new Queue<string>();

    orderQueue.Enqueue("Order_001");
    orderQueue.Enqueue("Order_002");
    ```
- Dequeue() — Remove an Item<br>
    Removes and returns the item at the front
    ```c#
    string customerId = customerIds.Dequeue();

    Console.WriteLine(customer);
    ```
- Peek() — Look at the First Item<br>
    lets you see the first item without removing it.
    ```c#
    string customerid = customerIds.Peek();
    ```
- Count <br>
    Tells how many items are currently in the queue
    ```c#
    Console.WriteLine(customerIds.Count);
    ```
- Contains() — Check if Item Exists
    ```c#
    if (customerIds.Contains(101))
    {
        Console.WriteLine("101 is in the queue");
    }
    ```
- Clear() — Remove Everything
    ```c#
    customers.Clear();
    ```
- TryDequeue()

    This is safer when the queue might be empty.
    ```c#
    ueue<string> customers = new Queue<string>();

    customers.Enqueue("Abc");

    if (customers.TryDequeue(out string customer))
    {
        Console.WriteLine($"Serving {customer}");
    }
    else
    {
        Console.WriteLine("Queue is empty");
    }
    ```
- TryPeek()

    you can safely look at the front using this
    ```c#
    if (customers.TryPeek(out string customer))
    {
        Console.WriteLine($"Next customer: {customer}");
    }
    else
    {
        Console.WriteLine("Queue is empty");
    }
    ```