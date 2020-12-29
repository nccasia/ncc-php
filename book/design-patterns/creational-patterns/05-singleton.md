#Singleton Pattern

#####Singleton Design Pattern: Singleton is a creational design pattern that lets you ensure that a class has only one instance, while providing a global access point to this instance.
- Singleton: The Singleton class declares the static method getInstance that returns the same instance of its own class.
  
  The Singleton’s constructor should be hidden from the client code. Calling the getInstance method should be the only way of getting the Singleton object.

![Alt text](../../images/design-patterns/creational-patterns/singleton-structure.png?raw=true "Prototype Pattern Structure")

Example:

```php
class Singleton
{
    private static $instances = [];

    protected function __construct() { }

    protected function __clone() { }

    public function __wakeup()
    {
        throw new \Exception("Cannot unserialize a singleton.");
    }

    public static function getInstance(): Singleton
    {
        $cls = static::class;
        if (!isset(self::$instances[$cls])) {
            self::$instances[$cls] = new static();
        }

        return self::$instances[$cls];
    }

    public function someBusinessLogic()
    {
        // ...
    }
}

/**
 * The client code.
 */
function clientCode()
{
    $s1 = Singleton::getInstance();
    $s2 = Singleton::getInstance();
    if ($s1 === $s2) {
        echo "Singleton works, both variables contain the same instance.";
    } else {
        echo "Singleton failed, variables contain different instances.";
    }
}

clientCode();
```
Output:

    Singleton works, both variables contain the same instance.
    
**Keyword: design pattern singleton**