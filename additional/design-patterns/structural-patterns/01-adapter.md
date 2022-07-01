#Adapter Pattern

**Adapter Pattern: Adapter is a structural design pattern that allows objects with incompatible interfaces to collaborate.**

An Abstract Factory Pattern includes the following basic components:
- **Object adapter**: This implementation uses the object composition principle: the adapter implements the interface of one object and wraps the other one. It can be implemented in all popular programming languages.
    - The Client is a class that contains the existing business logic of the program.
    - The Client Interface describes a protocol that other classes must follow to be able to collaborate with the client code.
    - The Service is some useful class (usually 3rd-party or legacy). The client can’t use this class directly because it has an incompatible interface.
    - The Adapter is a class that’s able to work with both the client and the service: it implements the client interface, while wrapping the service object. The adapter receives calls from the client via the adapter interface and translates them into calls to the wrapped service object in a format it can understand.
    - The client code doesn’t get coupled to the concrete adapter class as long as it works with the adapter via the client interface. Thanks to this, you can introduce new types of adapters into the program without breaking the existing client code. This can be useful when the interface of the service class gets changed or replaced: you can just create a new adapter class without changing the client code.
    
    ![Alt text](../../../basic/images/design-patterns/structural-patterns/structure-object-adapter.png?raw=true "Adapter Pattern Structure")

- **Class adapter**: This implementation uses inheritance: the adapter inherits interfaces from both objects at the same time. Note that this approach can only be implemented in programming languages that support multiple inheritance, such as C++.
    - The Class Adapter doesn’t need to wrap any objects because it inherits behaviors from both the client and the service. The adaptation happens within the overridden methods. The resulting adapter can be used in place of an existing client class.
    
    ![Alt text](../../../basic/images/design-patterns/structural-patterns/structure-class-adapter.png?raw=true "Adapter Pattern Structure")



Example:
```php
/**
 * The Target defines the domain-specific interface used by the client code.
 */
class Target
{
    public function request(): string
    {
        return "Target: The default target's behavior.";
    }
}

/**
 * The Adaptee contains some useful behavior, but its interface is incompatible
 * with the existing client code. The Adaptee needs some adaptation before the
 * client code can use it.
 */
class Adaptee
{
    public function specificRequest(): string
    {
        return ".eetpadA eht fo roivaheb laicepS";
    }
}

/**
 * The Adapter makes the Adaptee's interface compatible with the Target's
 * interface.
 */
class Adapter extends Target
{
    private $adaptee;

    public function __construct(Adaptee $adaptee)
    {
        $this->adaptee = $adaptee;
    }

    public function request(): string
    {
        return "Adapter: (TRANSLATED) " . strrev($this->adaptee->specificRequest());
    }
}

/**
 * The client code supports all classes that follow the Target interface.
 */
function clientCode(Target $target)
{
    echo $target->request();
}

echo "Client: I can work just fine with the Target objects:\n";
$target = new Target();
clientCode($target);
echo "\n\n";

$adaptee = new Adaptee();
echo "Client: The Adaptee class has a weird interface. See, I don't understand it:\n";
echo "Adaptee: " . $adaptee->specificRequest();
echo "\n\n";

echo "Client: But I can work with it via the Adapter:\n";
$adapter = new Adapter($adaptee);
clientCode($adapter);
```
Output:

    Client: I can work just fine with the Target objects:
    Target: The default target's behavior.
    
    Client: The Adaptee class has a weird interface. See, I don't understand it:
    Adaptee: .eetpadA eht fo roivaheb laicepS
    
    Client: But I can work with it via the Adapter:
    Adapter: (TRANSLATED) Special behavior of the Adaptee.
    
**Keyword: design pattern adapter**