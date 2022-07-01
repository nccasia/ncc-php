#Abstract Factory Pattern

**Abstract Factory Pattern: A design pattern that provides an interface for creating related or dependent objects without specifying their specific classes.**

An Abstract Factory Pattern includes the following basic components:

- AbstractFactory: Declaring the form of an interface or abstract class contains methods to create abstract objects.
- ConcreteFactory: Build and implement methods to create specific objects.
- AbstractProduct: Declare the form of an interface or abstract class to define abstract objects.
- Product: Implementation of specific objects, implementation of methods are specified in AbstractProduct.
- Client: The objects that use AbstractFactory and AbstractProduct.

![Alt text](../../images/design-patterns/creational-patterns/abstract-factory-structure.png?raw=true "Abstract Factory Pattern Structure")

Example:
```php
namespace AbstractFactory;

class ConcreteFactory1 implements AbstractFactory
{
    public function createProductA(): AbstractProductA
    {
        return new ConcreteProductA1();
    }

    public function createProductB(): AbstractProductB
    {
        return new ConcreteProductB1();
    }
}

class ConcreteFactory2 implements AbstractFactory
{
    public function createProductA(): AbstractProductA
    {
        return new ConcreteProductA2();
    }

    public function createProductB(): AbstractProductB
    {
        return new ConcreteProductB2();
    }
}

interface AbstractProductA
{
    public function usefulFunctionA(): string;
}

class ConcreteProductA1 implements AbstractProductA
{
    public function usefulFunctionA(): string
    {
        return "The result of the product A1.";
    }
}

class ConcreteProductA2 implements AbstractProductA
{
    public function usefulFunctionA(): string
    {
        return "The result of the product A2.";
    }
}

interface AbstractProductB
{
  
    public function anotherUsefulFunctionB(AbstractProductA $collaborator): string;
}

class ConcreteProductB1 implements AbstractProductB
{
    public function usefulFunctionB(): string
    {
        return "The result of the product B1.";
    }

    public function anotherUsefulFunctionB(AbstractProductA $collaborator): string
    {
        $result = $collaborator->usefulFunctionA();

        return "The result of the B1 collaborating with the ({$result})";
    }
}

class ConcreteProductB2 implements AbstractProductB
{
    public function usefulFunctionB(): string
    {
        return "The result of the product B2.";
    }

    public function anotherUsefulFunctionB(AbstractProductA $collaborator): string
    {
        $result = $collaborator->usefulFunctionA();

        return "The result of the B2 collaborating with the ({$result})";
    }
}

function clientCode(AbstractFactory $factory)
{
    $product_a = $factory->createProductA();
    $product_b = $factory->createProductB();

    print($product_b->usefulFunctionB() . "\n");
    print($product_b->anotherUsefulFunctionB($product_a) . "\n");
}

print("Client: Testing client code with the first factory type...\n");
clientCode(new ConcreteFactory1());

print("\n");

print("Client: Testing the same client code with the second factory type...\n");
clientCode(new ConcreteFactory2());
```
Output:

    Client: Testing client code with the first factory type...
    The result of the product B1.
    The result of the B1 collaborating with the (The result of the product A1.)
    
    Client: Testing the same client code with the second factory type...
    The result of the product B2.
    The result of the B2 collaborating with the (The result of the product A2.)
    
**Keyword: design pattern abstract factory**