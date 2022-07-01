#Abstract Factory Pattern

**Decorator is a structural design pattern that lets you attach new behaviors to objects by placing these objects inside special wrapper objects that contain the behaviors.**

An Abstract Factory Pattern includes the following basic components:

- The Component declares the common interface for both wrappers and wrapped objects.
- Concrete Component is a class of objects being wrapped. It defines the basic behavior, which can be altered by decorators.
- The Base Decorator class has a field for referencing a wrapped object. The field’s type should be declared as the component interface so it can contain both concrete components and decorators. The base decorator delegates all operations to the wrapped object.
- Concrete Decorators define extra behaviors that can be added to components dynamically. Concrete decorators override methods of the base decorator and execute their behavior either before or after calling the parent method.
- The Client can wrap components in multiple layers of decorators, as long as it works with all objects via the component interface.

![Alt text](../../../basic/images/design-patterns/structural-patterns/decorator-structure.png?raw=true "Abstract Factory Pattern Structure")

Example:
```php
/**
 * The base Component interface defines operations that can be altered by
 * decorators.
 */
interface Component
{
    public function operation(): string;
}

/**
 * Concrete Components provide default implementations of the operations. There
 * might be several variations of these classes.
 */
class ConcreteComponent implements Component
{
    public function operation(): string
    {
        return "ConcreteComponent";
    }
}

/**
 * The base Decorator class follows the same interface as the other components.
 * The primary purpose of this class is to define the wrapping interface for all
 * concrete decorators. The default implementation of the wrapping code might
 * include a field for storing a wrapped component and the means to initialize
 * it.
 */
class Decorator implements Component
{
    /**
     * @var Component
     */
    protected $component;

    public function __construct(Component $component)
    {
        $this->component = $component;
    }

    /**
     * The Decorator delegates all work to the wrapped component.
     */
    public function operation(): string
    {
        return $this->component->operation();
    }
}

/**
 * Concrete Decorators call the wrapped object and alter its result in some way.
 */
class ConcreteDecoratorA extends Decorator
{
    /**
     * Decorators may call parent implementation of the operation, instead of
     * calling the wrapped object directly. This approach simplifies extension
     * of decorator classes.
     */
    public function operation(): string
    {
        return "ConcreteDecoratorA(" . parent::operation() . ")";
    }
}

/**
 * Decorators can execute their behavior either before or after the call to a
 * wrapped object.
 */
class ConcreteDecoratorB extends Decorator
{
    public function operation(): string
    {
        return "ConcreteDecoratorB(" . parent::operation() . ")";
    }
}

/**
 * The client code works with all objects using the Component interface. This
 * way it can stay independent of the concrete classes of components it works
 * with.
 */
function clientCode(Component $component)
{
    // ...

    echo "RESULT: " . $component->operation();

    // ...
}

/**
 * This way the client code can support both simple components...
 */
$simple = new ConcreteComponent();
echo "Client: I've got a simple component:\n";
clientCode($simple);
echo "\n\n";

/**
 * ...as well as decorated ones.
 *
 * Note how decorators can wrap not only simple components but the other
 * decorators as well.
 */
$decorator1 = new ConcreteDecoratorA($simple);
$decorator2 = new ConcreteDecoratorB($decorator1);
echo "Client: Now I've got a decorated component:\n";
clientCode($decorator2);
```
Output:

    Client: I've got a simple component:
    RESULT: ConcreteComponent
    
    Client: Now I've got a decorated component:
    RESULT: ConcreteDecoratorB(ConcreteDecoratorA(ConcreteComponent))
    
**Keyword: design pattern bridge**