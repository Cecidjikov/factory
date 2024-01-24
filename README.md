using System;

// Интерфейс за кафе
public interface ICoffee
{
    void GrindCoffee();
    void MakeCoffee();
    void PourIntoCup();
}

// Клас за Espresso кафе
public class Espresso : ICoffee
{
    public void GrindCoffee()
    {
        Console.WriteLine("Grinding espresso coffee beans.");
    }

    public void MakeCoffee()
    {
        Console.WriteLine("Making espresso.");
    }

    public void PourIntoCup()
    {
        Console.WriteLine("Pouring espresso into the cup.");
    }
}

// Клас за Cappuccino кафе
public class Cappuccino : ICoffee
{
    public void GrindCoffee()
    {
        Console.WriteLine("Grinding cappuccino coffee beans.");
    }

    public void MakeCoffee()
    {
        Console.WriteLine("Making cappuccino.");
    }

    public void PourIntoCup()
    {
        Console.WriteLine("Pouring cappuccino into the cup.");
    }
}

// Клас за Americano кафе
public class Americano : ICoffee
{
    public void GrindCoffee()
    {
        Console.WriteLine("Grinding Americano coffee beans.");
    }

    public void MakeCoffee()
    {
        Console.WriteLine("Making Americano.");
    }

    public void PourIntoCup()
    {
        Console.WriteLine("Pouring Americano into the cup.");
    }
}

// Фабрика за създаване на кафе
public class CoffeeFactory
{
    public ICoffee CreateCoffee(string type)
    {
        switch (type.ToLower())
        {
            case "espresso":
                return new Espresso();
            case "cappuccino":
                return new Cappuccino();
            case "americano":
                return new Americano();
            default:
                throw new ArgumentException("Invalid coffee type.");
        }
    }
}

class Program
{
    static void Main()
    {
        // Създаване на фабрика
        CoffeeFactory coffeeFactory = new CoffeeFactory();

        // Поръчване на кафе
        ICoffee espresso = coffeeFactory.CreateCoffee("espresso");
        ProcessCoffee(espresso);

        ICoffee cappuccino = coffeeFactory.CreateCoffee("cappuccino");
        ProcessCoffee(cappuccino);

        ICoffee americano = coffeeFactory.CreateCoffee("americano");
        ProcessCoffee(americano);

      
    }

    static void ProcessCoffee(ICoffee coffee)
    {
        Console.WriteLine("\nProcessing coffee order:");
        coffee.GrindCoffee();
        coffee.MakeCoffee();
        coffee.PourIntoCup();
        Console.WriteLine();
    }
}
