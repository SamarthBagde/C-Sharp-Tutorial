# Encapsulation

`Encapsulation` is the object-oriented programming mechanism of bundling data (fields) and the methods operating on that data into a single unit (a class) while restricting direct access to the internal state.

```c#
class BankAccount
{
    private decimal balance;

    public decimal GetBalance()
    {
        return balance;
    }

    public void Deposit(decimal amount)
    {
        if (amount > 0)
        {
            balance += amount;
        }
    }
}
```