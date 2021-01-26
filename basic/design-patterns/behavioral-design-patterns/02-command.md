#Command

**Command is a behavioral design pattern that turns a request into a stand-alone object that contains all information about the request. This transformation lets you parameterize methods with different requests, delay or queue a request’s execution, and support undoable operations.**

An Abstract Factory Pattern includes the following basic components:

- The Sender class (aka invoker) is responsible for initiating requests. This class must have a field for storing a reference to a command object. The sender triggers that command instead of sending the request directly to the receiver. Note that the sender isn’t responsible for creating the command object. Usually, it gets a pre-created command from the client via the constructor.
- The Command interface usually declares just a single method for executing the command.
- Concrete Commands implement various kinds of requests. A concrete command isn’t supposed to perform the work on its own, but rather to pass the call to one of the business logic objects. However, for the sake of simplifying the code, these classes can be merged.
  Parameters required to execute a method on a receiving object can be declared as fields in the concrete command. You can make command objects immutable by only allowing the initialization of these fields via the constructor.
- The Receiver class contains some business logic. Almost any object may act as a receiver. Most commands only handle the details of how a request is passed to the receiver, while the receiver itself does the actual work.
- The Client creates and configures concrete command objects. The client must pass all of the request parameters, including a receiver instance, into the command’s constructor. After that, the resulting command may be associated with one or multiple senders.

![Alt text](../../images/design-patterns/behavioral-design-patterns/command-structure.png?raw=true "Abstract Factory Pattern Structure")

Example:
```php

/**
 * The Command interface declares a method for executing a command.
 */
interface Command
{
    public function execute(): void;
}

/**
 * Some commands can implement simple operations on their own.
 */
class SimpleCommand implements Command
{
    private $payload;

    public function __construct(string $payload)
    {
        $this->payload = $payload;
    }

    public function execute(): void
    {
        echo "SimpleCommand: See, I can do simple things like printing (" . $this->payload . ")\n";
    }
}

/**
 * However, some commands can delegate more complex operations to other objects,
 * called "receivers."
 */
class ComplexCommand implements Command
{
    /**
     * @var Receiver
     */
    private $receiver;

    /**
     * Context data, required for launching the receiver's methods.
     */
    private $a;

    private $b;

    /**
     * Complex commands can accept one or several receiver objects along with
     * any context data via the constructor.
     */
    public function __construct(Receiver $receiver, string $a, string $b)
    {
        $this->receiver = $receiver;
        $this->a = $a;
        $this->b = $b;
    }

    /**
     * Commands can delegate to any methods of a receiver.
     */
    public function execute(): void
    {
        echo "ComplexCommand: Complex stuff should be done by a receiver object.\n";
        $this->receiver->doSomething($this->a);
        $this->receiver->doSomethingElse($this->b);
    }
}

/**
 * The Receiver classes contain some important business logic. They know how to
 * perform all kinds of operations, associated with carrying out a request. In
 * fact, any class may serve as a Receiver.
 */
class Receiver
{
    public function doSomething(string $a): void
    {
        echo "Receiver: Working on (" . $a . ".)\n";
    }

    public function doSomethingElse(string $b): void
    {
        echo "Receiver: Also working on (" . $b . ".)\n";
    }
}

/**
 * The Invoker is associated with one or several commands. It sends a request to
 * the command.
 */
class Invoker
{
    /**
     * @var Command
     */
    private $onStart;

    /**
     * @var Command
     */
    private $onFinish;

    /**
     * Initialize commands.
     */
    public function setOnStart(Command $command): void
    {
        $this->onStart = $command;
    }

    public function setOnFinish(Command $command): void
    {
        $this->onFinish = $command;
    }

    /**
     * The Invoker does not depend on concrete command or receiver classes. The
     * Invoker passes a request to a receiver indirectly, by executing a
     * command.
     */
    public function doSomethingImportant(): void
    {
        echo "Invoker: Does anybody want something done before I begin?\n";
        if ($this->onStart instanceof Command) {
            $this->onStart->execute();
        }

        echo "Invoker: ...doing something really important...\n";

        echo "Invoker: Does anybody want something done after I finish?\n";
        if ($this->onFinish instanceof Command) {
            $this->onFinish->execute();
        }
    }
}

/**
 * The client code can parameterize an invoker with any commands.
 */
$invoker = new Invoker();
$invoker->setOnStart(new SimpleCommand("Say Hi!"));
$receiver = new Receiver();
$invoker->setOnFinish(new ComplexCommand($receiver, "Send email", "Save report"));

$invoker->doSomethingImportant();
```
Output:

    Invoker: Does anybody want something done before I begin?
    SimpleCommand: See, I can do simple things like printing (Say Hi!)
    Invoker: ...doing something really important...
    Invoker: Does anybody want something done after I finish?
    ComplexCommand: Complex stuff should be done by a receiver object.
    Receiver: Working on (Send email.)
    Receiver: Also working on (Save report.)
    
**Keyword: design pattern abstract factory**