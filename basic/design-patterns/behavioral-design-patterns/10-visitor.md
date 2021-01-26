#Visitor

**Visitor is a behavioral design pattern that lets you separate algorithms from the objects on which they operate.**

An Abstract Factory Pattern includes the following basic components:

1. The Visitor interface declares a set of visiting methods that can take concrete elements of an object structure as arguments. These methods may have the same names if the program is written in a language that supports overloading, but the type of their parameters must be different.

2. Each Concrete Visitor implements several versions of the same behaviors, tailored for different concrete element classes.

3. The Element interface declares a method for “accepting” visitors. This method should have one parameter declared with the type of the visitor interface.

4. Each Concrete Element must implement the acceptance method. The purpose of this method is to redirect the call to the proper visitor’s method corresponding to the current element class. Be aware that even if a base element class implements this method, all subclasses must still override this method in their own classes and call the appropriate method on the visitor object.

5. The Client usually represents a collection or some other complex object (for example, a Composite tree). Usually, clients aren’t aware of all the concrete element classes because they work with objects from that collection via some abstract interface.
  
![Alt text](../../images/design-patterns/behavioral-design-patterns/visitor-structure.png?raw=true "Abstract Factory Pattern Structure")

Example:
```php

/**
 * The Component interface declares an `accept` method that should take the base
 * visitor interface as an argument.
 */
interface Component
{
    public function accept(Visitor $visitor): void;
}

/**
 * Each Concrete Component must implement the `accept` method in such a way that
 * it calls the visitor's method corresponding to the component's class.
 */
class ConcreteComponentA implements Component
{
    /**
     * Note that we're calling `visitConcreteComponentA`, which matches the
     * current class name. This way we let the visitor know the class of the
     * component it works with.
     */
    public function accept(Visitor $visitor): void
    {
        $visitor->visitConcreteComponentA($this);
    }

    /**
     * Concrete Components may have special methods that don't exist in their
     * base class or interface. The Visitor is still able to use these methods
     * since it's aware of the component's concrete class.
     */
    public function exclusiveMethodOfConcreteComponentA(): string
    {
        return "A";
    }
}

class ConcreteComponentB implements Component
{
    /**
     * Same here: visitConcreteComponentB => ConcreteComponentB
     */
    public function accept(Visitor $visitor): void
    {
        $visitor->visitConcreteComponentB($this);
    }

    public function specialMethodOfConcreteComponentB(): string
    {
        return "B";
    }
}

/**
 * The Visitor Interface declares a set of visiting methods that correspond to
 * component classes. The signature of a visiting method allows the visitor to
 * identify the exact class of the component that it's dealing with.
 */
interface Visitor
{
    public function visitConcreteComponentA(ConcreteComponentA $element): void;

    public function visitConcreteComponentB(ConcreteComponentB $element): void;
}

/**
 * Concrete Visitors implement several versions of the same algorithm, which can
 * work with all concrete component classes.
 *
 * You can experience the biggest benefit of the Visitor pattern when using it
 * with a complex object structure, such as a Composite tree. In this case, it
 * might be helpful to store some intermediate state of the algorithm while
 * executing visitor's methods over various objects of the structure.
 */
class ConcreteVisitor1 implements Visitor
{
    public function visitConcreteComponentA(ConcreteComponentA $element): void
    {
        echo $element->exclusiveMethodOfConcreteComponentA() . " + ConcreteVisitor1\n";
    }

    public function visitConcreteComponentB(ConcreteComponentB $element): void
    {
        echo $element->specialMethodOfConcreteComponentB() . " + ConcreteVisitor1\n";
    }
}

class ConcreteVisitor2 implements Visitor
{
    public function visitConcreteComponentA(ConcreteComponentA $element): void
    {
        echo $element->exclusiveMethodOfConcreteComponentA() . " + ConcreteVisitor2\n";
    }

    public function visitConcreteComponentB(ConcreteComponentB $element): void
    {
        echo $element->specialMethodOfConcreteComponentB() . " + ConcreteVisitor2\n";
    }
}

/**
 * The client code can run visitor operations over any set of elements without
 * figuring out their concrete classes. The accept operation directs a call to
 * the appropriate operation in the visitor object.
 */
function clientCode(array $components, Visitor $visitor)
{
    // ...
    foreach ($components as $component) {
        $component->accept($visitor);
    }
    // ...
}

$components = [
    new ConcreteComponentA(),
    new ConcreteComponentB(),
];

echo "The client code works with all visitors via the base Visitor interface:\n";
$visitor1 = new ConcreteVisitor1();
clientCode($components, $visitor1);
echo "\n";

echo "It allows the same client code to work with different types of visitors:\n";
$visitor2 = new ConcreteVisitor2();
clientCode($components, $visitor2);
```
Output:

    The client code works with all visitors via the base Visitor interface:
    A + ConcreteVisitor1
    B + ConcreteVisitor1
    
    It allows the same client code to work with different types of visitors:
    A + ConcreteVisitor1
    B + ConcreteVisitor2
    
**Keyword: design pattern abstract factory**