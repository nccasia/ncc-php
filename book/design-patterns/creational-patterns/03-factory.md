#Builder Pattern

#####Builder Design Pattern: is a creational design pattern that separate the construction of a complex object from its representation so that the same construction process can create different representations.
- Product : Represents the object to be created, this object is complex, has many properties..
- Builder : It's an abstract class or an interface that declares the method of creating an object.
- ConcreteBuilder : Inherit Builder and install detailed how the object is created. It identifies and holds the instances it creates, and it also provides a method to return the instances it created earlier..
- Director/ Client: Where is the place that will call the Builder to create the object.

![Alt text](../../images/design-patterns/creational-patterns/factory-method-structure.png?raw=true "Abstract Factory Pattern Structure")

Example:

```php
abstract class Creator
{
    abstract public function factoryMethod(): Product;

    
    public function someOperation(): string
    {
        // Call the factory method to create a Product object.
        $product = $this->factoryMethod();
        // Now, use the product.
        $result = "Creator: The same creator's code has just worked with " .
            $product->operation();

        return $result;
    }
}

class ConcreteCreator1 extends Creator
{
    public function factoryMethod(): Product
    {
        return new ConcreteProduct1();
    }
}

class ConcreteCreator2 extends Creator
{
    public function factoryMethod(): Product
    {
        return new ConcreteProduct2();
    }
}

interface Product
{
    public function operation(): string;
}

class ConcreteProduct1 implements Product
{
    public function operation(): string
    {
        return "{Result of the ConcreteProduct1}";
    }
}

class ConcreteProduct2 implements Product
{
    public function operation(): string
    {
        return "{Result of the ConcreteProduct2}";
    }
}

function clientCode(Creator $creator)
{
    // ...
    echo "Client: I'm not aware of the creator's class, but it still works.\n"
        . $creator->someOperation();
    // ...
}

echo "App: Launched with the ConcreteCreator1.\n";
clientCode(new ConcreteCreator1());
echo "\n\n";

echo "App: Launched with the ConcreteCreator2.\n";
clientCode(new ConcreteCreator2());
```
Output:

    App: Launched with the ConcreteCreator1.
    Client: I'm not aware of the creator's class, but it still works.
    Creator: The same creator's code has just worked with {Result of the ConcreteProduct1}
    
    App: Launched with the ConcreteCreator2.
    Client: I'm not aware of the creator's class, but it still works.
    Creator: The same creator's code has just worked with {Result of the ConcreteProduct2}
    
**Keyword: design pattern factory method**