- [OOP](#oop)
  - [1. What's OOP?](#1-whats-oop)
  - [2. Basic properties](#2-basic-properties)
- [Design Pattern](#design-pattern)
  - [1. What's Design pattern?](#1-whats-design-pattern)
  - [2. Classification of design patterns](#2-classification-of-design-patterns)
        - [Creational Patterns](#creational-patterns)
        - [Structural Patterns](#structural-patterns)
        - [Behavioral Patterns](#behavioral-patterns)
  - [3. Some popular patterns:](#3-some-popular-patterns)
    - [3.1. Factory](#31-factory)
    - [3.2. Singleton](#32-singleton)
    - [3.3. Repository](#33-repository)
    - [3.4. Decorator](#34-decorator)
    - [3.5. Observer](#35-observer)
    - [3.6. Strategy](#36-strategy)


# OOP

## 1. What's OOP?

OOP Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data and code: 
 - data in the form of fields (often known as attributes or properties)
 - code, in the form of procedures (often known as methods).

It can be understood that OOP is a set of functions in a class and this class will be used to process data of a particular object or objects that share properties.

Example:
```php
    class Person() {
        private $name;
        private $age;
    
        public function setName($name){
            $this->name = $name;
            return $this;
        }
        
        public function getName(){
            return $this->name;
        }
        
        public function setAge($age){
            $this->age = $age;
            return $this;
        }
        
        public function getAge(){
            return $this->age;
        }
        //..
    }
```

The above class handles all objects that have the attributes "name" and "age".

## 2. Basic properties

**Abstraction**: Abstraction is one of the key concepts of object-oriented programming (OOP) languages. Its main goal is to handle complexity by hiding unnecessary details from the user. That enables the user to implement more complex logic on top of the provided abstraction without understanding or even thinking about all the hidden complexity.

**Encapsulation**: encapsulation refers to the bundling of data with the methods that operate on that data, or the restricting of direct access to some of an object's components.

 - Encapsulation is used to hide the values or state of a structured data object inside a class, preventing unauthorized parties' direct access to them. 
 - Publicly accessible methods are generally provided in the class (so-called "getters" and "setters") to access the values, and other client classes call these methods to retrieve and modify the values within the object.

**Polymorphism**: Polymorphism is one of the core concepts in OOP languages. It describes the concept that different classes can be used with the same interface. Each of these classes can provide its own implementation of the interface.

**Inheritance**: Inheritance is one of the core concepts of object-oriented programming (OOP) languages. It is a mechanism where you can to derive a class from another class for a hierarchy of classes that share a set of attributes and methods.

# Design Pattern

## 1. What's Design pattern?

Design pattern is a general repeatable solution to a commonly occurring problem in software design. A design pattern isn't a finished design that can be transformed directly into code. It is a description or template for how to solve a problem that can be used in many different situations.

## 2. Classification of design patterns

The design pattern system is divided into 3 groups: Creational (5 models), Structural (7 models) and Behavioral (11 models).

Creational patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code.

##### Creational Patterns
    Abstract Factory
    Builder
    Factory
    Prototype
    Singleton

Structural patterns explain how to assemble objects and classes into larger structures while keeping these structures flexible and efficient.
##### Structural Patterns
    Adapter
    Bridge
    Composite
    Decorator
    Facade
    Flyweight
    Proxy

Behavioral design patterns are concerned with algorithms and the assignment of responsibilities between objects.
##### Behavioral Patterns
    Chain of responsibility
    Command
    Interpreter
    Iterator
    Mediator
    Memento
    Observer
    State
    Strategy
    Template method
    Visitor
    Repository
    
## 3. Some popular patterns:

### 3.1. Factory

The factory pattern in PHP is a design pattern that provides a way to create objects without specifying the exact class of object that will be created. Instead, a factory class is responsible for creating objects based on a set of predefined rules or conditions. This allows for greater flexibility in the creation of objects, as the exact class of object that is created can be determined at runtime based on input data or other factors. The factory pattern is often used in conjunction with dependency injection to further increase flexibility and ease of use.

```php
interface Shape {
  public function draw();
}

class Rectangle implements Shape {
  public function draw() {
    echo "Drawing a rectangle\n";
  }
}

class Circle implements Shape {
  public function draw() {
    echo "Drawing a circle\n";
  }
}

class ShapeFactory {
  public function getShape(string $shapeType): Shape {
    if ($shapeType == null) {
      return null;
    }
    if (strtolower($shapeType) == "circle") {
      return new Circle();
    } else if (strtolower($shapeType) == "rectangle") {
      return new Rectangle();
    }
    return null;
  }
}

$factory = new ShapeFactory();
$shape = $factory->getShape("CIRCLE");
$shape->draw();
$shape = $factory->getShape("RECTANGLE");
$shape->draw();
```

### 3.2. Singleton

The singleton pattern in PHP is a design pattern that ensures that a class has only one instance, while providing a global access point to this instance. 

```php
class Singleton {
    private static $instance;

    /**
     * The Singleton's constructor should always be private to prevent direct
     * construction calls with the `new` operator.
     */
    protected function __construct() { }

    /**
     * Singletons should not be cloneable.
     */
    protected function __clone() { }

    /**
     * Singletons should not be restorable from strings.
     */
    public function __wakeup()
    {
        throw new \Exception("Cannot unserialize a singleton.");
    }

    public static function getInstance(): Singleton {
        if (null === static::$instance) {
            static::$instance = new static();
        }
        return static::$instance;
    }
}
```

It is important to note that, Singleton is considered an anti-pattern and should be avoided in most cases as it creates global state, hard to test and make the code hard to reason about, instead you can use dependency injection to manage the dependencies of your objects.

### 3.3. Repository

The repository pattern provides a way to separate the logic of data access from the business logic of the application. The repository pattern defines a class that acts as an intermediary between the data source (e.g. a database) and the rest of the application. 

```php
interface Repository {
    public function find(int $id);
    public function findAll();
    public function save($data);
    public function delete(int $id);
}

class UserRepository implements Repository {
    private $pdo;

    public function __construct(\PDO $pdo) {
        $this->pdo = $pdo;
    }

    public function find(int $id) {
        $stmt = $this->pdo->prepare("SELECT * FROM users WHERE id = ?");
        $stmt->execute([$id]);
        return $stmt->fetch();
    }

    public function findAll() {
        $stmt = $this->pdo->prepare("SELECT * FROM users");
        $stmt->execute();
        return $stmt->fetchAll();
    }

    public function save($data) {
        if (isset($data['id'])) {
            $stmt = $this->pdo->prepare("UPDATE users SET name = ?, email = ? WHERE id = ?");
            $stmt->execute([$data['name'], $data['email'], $data['id']]);
        } else {
            $stmt = $this->pdo->prepare("INSERT INTO users (name, email) VALUES (?, ?)");
            $stmt->execute([$data['name'], $data['email']]);
        }
    }

    public function delete(int $id) {
        $stmt = $this->pdo->prepare("DELETE FROM users WHERE id = ?");
        $stmt->execute([$id]);
    }
}
```

### 3.4. Decorator

The decorator pattern in PHP is a design pattern that allows you to add new functionality to an existing object without modifying its class. This is done by creating a decorator class that wraps the existing object and adds new methods or behavior. 

```php
interface Car {
    public function assemble();
}

class BasicCar implements Car {
    public function assemble() {
        return "Basic Car.";
    }
}

class CarDecorator implements Car {
    protected $car;
    public function __construct(Car $car) {
        $this->car = $car;
    }
    public function assemble() {
        return $this->car->assemble();
    }
}

class SportsCar extends CarDecorator {
    public function assemble() {
        return $this->car->assemble() . " Adding features of Sports Car.";
    }
}

class LuxuryCar extends CarDecorator {
    public function assemble() {
        return $this->car->assemble() . " Adding features of Luxury Car.";
    }
}
```

### 3.5. Observer

The observer pattern allows objects to be notified of changes to other objects. The basic idea is to create a subject object that other objects can observe, and when the subject object changes, it notifies all of its observers, without the objects being tightly coupled. 

### 3.6. Strategy

The strategy pattern allows you to change the behavior of an object at runtime by switching between different implementations of an interface. The strategy pattern is often used to create flexible and reusable code, and to encapsulate algorithms in a way that makes it easy to swap one algorithm for another.

