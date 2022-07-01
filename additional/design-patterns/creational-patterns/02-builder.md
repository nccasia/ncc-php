#Builder Pattern

#####Builder Design Pattern: is a creational design pattern that separate the construction of a complex object from its representation so that the same construction process can create different representations.
- Product : The Product declares the interface, which is common to all objects that can be produced by the creator and its subclasses.
- ConcreteProducts : Concrete Products are different implementations of the product interface..
- Creator: declares the factory method that returns new product objects. It’s important that the return type of this method matches the product interface. You can declare the factory method as abstract to force all subclasses to implement their own versions of the method. As an alternative, the base factory method can return some default product type.
    
    - Note, despite its name, product creation is not the primary responsibility of the creator. Usually, the creator class already has some core business logic related to products. The factory method helps to decouple this logic from the concrete product classes. Here is an analogy: a large software development company can have a training department for programmers. However, the primary function of the company as a whole is still writing code, not producing programmers.

- Director/ Client: Where is the place that will call the Builder to create the object.

![Alt text](../../images/design-patterns/creational-patterns/abstract-factory-structure.png?raw=true "Abstract Factory Pattern Structure")

Example:

```php
    interface Builder
    {
        public function producePartA(): void;
    
        public function producePartB(): void;
    
        public function producePartC(): void;
    }
    
    class ConcreteBuilder1 implements Builder
    {
        private $product;
    
        public function __construct()
        {
            $this->reset();
        }
    
        public function reset(): void
        {
            $this->product = new Product1();
        }
    
        public function producePartA(): void
        {
            $this->product->parts[] = "PartA1";
        }
    
        public function producePartB(): void
        {
            $this->product->parts[] = "PartB1";
        }
    
        public function producePartC(): void
        {
            $this->product->parts[] = "PartC1";
        }
    
        public function getProduct(): Product1
        {
            $result = $this->product;
            $this->reset();
    
            return $result;
        }
    }
    
    class Product1
    {
        public $parts = [];
    
        public function listParts(): void
        {
            echo "Product parts: " . implode(', ', $this->parts) . "\n\n";
        }
    }
    
    class Director
    {
        /**
         * @var Builder
         */
        private $builder;
    
        public function setBuilder(Builder $builder): void
        {
            $this->builder = $builder;
        }
    
        public function buildMinimalViableProduct(): void
        {
            $this->builder->producePartA();
        }
    
        public function buildFullFeaturedProduct(): void
        {
            $this->builder->producePartA();
            $this->builder->producePartB();
            $this->builder->producePartC();
        }
    }
    
    function clientCode(Director $director)
    {
        $builder = new ConcreteBuilder1();
        $director->setBuilder($builder);
    
        echo "Standard basic product:\n";
        $director->buildMinimalViableProduct();
        $builder->getProduct()->listParts();
    
        echo "Standard full featured product:\n";
        $director->buildFullFeaturedProduct();
        $builder->getProduct()->listParts();
    
        // Remember, the Builder pattern can be used without a Director class.
        echo "Custom product:\n";
        $builder->producePartA();
        $builder->producePartC();
        $builder->getProduct()->listParts();
    }
    
    $director = new Director();
    clientCode($director);
```
Output:

    Standard basic product:
    Product parts: PartA1
    
    Standard full featured product:
    Product parts: PartA1, PartB1, PartC1
    
    Custom product:
    Product parts: PartA1, PartC1
    
**Keyword: design pattern builder**