#Memento

**Memento is a behavioral design pattern that lets you save and restore the previous state of an object without revealing the details of its implementation.**

An Abstract Factory Pattern includes the following basic components:

1. Implementation based on nested classes
The classic implementation of the pattern relies on support for nested classes, available in many popular programming languages (such as C++, C#, and Java).
    - The Originator class can produce snapshots of its own state, as well as restore its state from snapshots when needed.
    - The Memento is a value object that acts as a snapshot of the originator’s state. It’s a common practice to make the memento immutable and pass it the data only once, via the constructor.
    - The Caretaker knows not only “when” and “why” to capture the originator’s state, but also when the state should be restored.
      A caretaker can keep track of the originator’s history by storing a stack of mementos. When the originator has to travel back in history, the caretaker fetches the topmost memento from the stack and passes it to the originator’s restoration method.
    - In this implementation, the memento class is nested inside the originator. This lets the originator access the fields and methods of the memento, even though they’re declared private. On the other hand, the caretaker has very limited access to the memento’s fields and methods, which lets it store mementos in a stack but not tamper with their state.

  From a component’s perspective, it all looks like a total black box. The sender doesn’t know who’ll end up handling its request, and the receiver doesn’t know who sent the request in the first place.
  
![Alt text](../../images/design-patterns/behavioral-design-patterns/memento-implementation-based-on-nested-classess-tructure.png?raw=true "Abstract Factory Pattern Structure")

2. Implementation based on an intermediate interface: There’s an alternative implementation, suitable for programming languages that don’t support nested classes
    - In the absence of nested classes, you can restrict access to the memento’s fields by establishing a convention that caretakers can work with a memento only through an explicitly declared intermediary interface, which would only declare methods related to the memento’s metadata.
    - On the other hand, originators can work with a memento object directly, accessing fields and methods declared in the memento class. The downside of this approach is that you need to declare all members of the memento public.
![Alt text](../../images/design-patterns/behavioral-design-patterns/memento-implementation-based-on-intermediate-interface.png?raw=true "Abstract Factory Pattern Structure")

3. Implementation with even stricter encapsulation : There’s another implementation which is useful when you don’t want to leave even the slightest chance of other classes accessing the state of the originator through the memento.
    - This implementation allows having multiple types of originators and mementos. Each originator works with a corresponding memento class. Neither originators nor mementos expose their state to anyone.
    - Caretakers are now explicitly restricted from changing the state stored in mementos. Moreover, the caretaker class becomes independent from the originator because the restoration method is now defined in the memento class.
    - Each memento becomes linked to the originator that produced it. The originator passes itself to the memento’s constructor, along with the values of its state. Thanks to the close relationship between these classes, a memento can restore the state of its originator, given that the latter has defined the appropriate
![Alt text](../../images/design-patterns/behavioral-design-patterns/memento-implementation-with-even-stricter-encapsulation.png?raw=true "Abstract Factory Pattern Structure")    
Example:
```php
/**
 * The Originator holds some important state that may change over time. It also
 * defines a method for saving the state inside a memento and another method for
 * restoring the state from it.
 */
class Originator
{
    /**
     * @var string For the sake of simplicity, the originator's state is stored
     * inside a single variable.
     */
    private $state;

    public function __construct(string $state)
    {
        $this->state = $state;
        echo "Originator: My initial state is: {$this->state}\n";
    }

    /**
     * The Originator's business logic may affect its internal state. Therefore,
     * the client should backup the state before launching methods of the
     * business logic via the save() method.
     */
    public function doSomething(): void
    {
        echo "Originator: I'm doing something important.\n";
        $this->state = $this->generateRandomString(30);
        echo "Originator: and my state has changed to: {$this->state}\n";
    }

    private function generateRandomString(int $length = 10): string
    {
        return substr(
            str_shuffle(
                str_repeat(
                    $x = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ',
                    ceil($length / strlen($x))
                )
            ),
            1,
            $length,
        );
    }

    /**
     * Saves the current state inside a memento.
     */
    public function save(): Memento
    {
        return new ConcreteMemento($this->state);
    }

    /**
     * Restores the Originator's state from a memento object.
     */
    public function restore(Memento $memento): void
    {
        $this->state = $memento->getState();
        echo "Originator: My state has changed to: {$this->state}\n";
    }
}

/**
 * The Memento interface provides a way to retrieve the memento's metadata, such
 * as creation date or name. However, it doesn't expose the Originator's state.
 */
interface Memento
{
    public function getName(): string;

    public function getDate(): string;
}

/**
 * The Concrete Memento contains the infrastructure for storing the Originator's
 * state.
 */
class ConcreteMemento implements Memento
{
    private $state;

    private $date;

    public function __construct(string $state)
    {
        $this->state = $state;
        $this->date = date('Y-m-d H:i:s');
    }

    /**
     * The Originator uses this method when restoring its state.
     */
    public function getState(): string
    {
        return $this->state;
    }

    /**
     * The rest of the methods are used by the Caretaker to display metadata.
     */
    public function getName(): string
    {
        return $this->date . " / (" . substr($this->state, 0, 9) . "...)";
    }

    public function getDate(): string
    {
        return $this->date;
    }
}

/**
 * The Caretaker doesn't depend on the Concrete Memento class. Therefore, it
 * doesn't have access to the originator's state, stored inside the memento. It
 * works with all mementos via the base Memento interface.
 */
class Caretaker
{
    /**
     * @var Memento[]
     */
    private $mementos = [];

    /**
     * @var Originator
     */
    private $originator;

    public function __construct(Originator $originator)
    {
        $this->originator = $originator;
    }

    public function backup(): void
    {
        echo "\nCaretaker: Saving Originator's state...\n";
        $this->mementos[] = $this->originator->save();
    }

    public function undo(): void
    {
        if (!count($this->mementos)) {
            return;
        }
        $memento = array_pop($this->mementos);

        echo "Caretaker: Restoring state to: " . $memento->getName() . "\n";
        try {
            $this->originator->restore($memento);
        } catch (\Exception $e) {
            $this->undo();
        }
    }

    public function showHistory(): void
    {
        echo "Caretaker: Here's the list of mementos:\n";
        foreach ($this->mementos as $memento) {
            echo $memento->getName() . "\n";
        }
    }
}

/**
 * Client code.
 */
$originator = new Originator("Super-duper-super-puper-super.");
$caretaker = new Caretaker($originator);

$caretaker->backup();
$originator->doSomething();

$caretaker->backup();
$originator->doSomething();

$caretaker->backup();
$originator->doSomething();

echo "\n";
$caretaker->showHistory();

echo "\nClient: Now, let's rollback!\n\n";
$caretaker->undo();

echo "\nClient: Once more!\n\n";
$caretaker->undo();
```
Output:

    Originator: My initial state is: Super-duper-super-puper-super. 
    
    Caretaker: Saving Originator's state...
    Originator: I'm doing something important.
    Originator: and my state has changed to: srGIngezAEboNPDjBkuvymJKUtMSFX
    
    Caretaker: Saving Originator's state...
    Originator: I'm doing something important.
    Originator: and my state has changed to: UwCZQaHJOiERLlchyVuMbXNtpqTgWF
    
    Caretaker: Saving Originator's state...
    Originator: I'm doing something important.
    Originator: and my state has changed to: incqsdoJXkbDUuVOvRFYyKBgfzwZCQ
    
    Caretaker: Here's the list of mementos:
    2018-06-04 14:50:39 / (Super-dup...)
    2018-06-04 14:50:39 / (srGIngezA...)
    2018-06-04 14:50:39 / (UwCZQaHJO...)
    
    Client: Now, let's rollback!
    
    Caretaker: Restoring state to: 2018-06-04 14:50:39 / (UwCZQaHJO...)
    Originator: My state has changed to: UwCZQaHJOiERLlchyVuMbXNtpqTgWF
    
    Client: Once more!
    
    Caretaker: Restoring state to: 2018-06-04 14:50:39 / (srGIngezA...)
    Originator: My state has changed to: srGIngezAEboNPDjBkuvymJKUtMSFX
    
**Keyword: design pattern abstract factory**