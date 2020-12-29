# OOP

## 1. What's OOP?

**OOP Object-oriented programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data and code: data in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods).**

It can be understood that OOP is a set of functions in a class and this class will be used to process data of a particular object or objects that share properties.

Example:
```php
    class Person()
    {
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

**Encapsulation**: encapsulation refers to the bundling of data with the methods that operate on that data, or the restricting of direct access to some of an object's components.[1] Encapsulation is used to hide the values or state of a structured data object inside a class, preventing unauthorized parties' direct access to them. Publicly accessible methods are generally provided in the class (so-called "getters" and "setters") to access the values, and other client classes call these methods to retrieve and modify the values within the object..

**Polymorphism**: Polymorphism is one of the core concepts in OOP languages. It describes the concept that different classes can be used with the same interface. Each of these classes can provide its own implementation of the interface.

**Inheritance**: Inheritance is one of the core concepts of object-oriented programming (OOP) languages. It is a mechanism where you can to derive a class from another class for a hierarchy of classes that share a set of attributes and methods.

# Design Pattern

### **1. What's Design pattern?**

Design pattern is a general repeatable solution to a commonly occurring problem in software design. A design pattern isn't a finished design that can be transformed directly into code. It is a description or template for how to solve a problem that can be used in many different situations.

### **2. Classification of design patterns**

The design pattern system is divided into 3 groups: Creational (5 models), Structural (7 models) and Behavioral (11 models).

##### Creational Patterns
    Abstract Factory
    Builder
    Factory
    Prototype
    Singleton

##### Structural Patterns
    Adapter
    Bridge
    Composite
    Decorator
    Facade
    Flyweight
    Proxy

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
    
#**3. Creational Design Patterns**
**Creational patterns provide various object creation mechanisms, which increase flexibility and reuse of existing code.**

#####[1. Abstract Factory Pattern](design-patterns/creational-patterns/01-abstract-factory.md)  

#####[2. Builder Design Pattern](design-patterns/creational-patterns/02-builder.md)
    
#####[3. Factory Pattern (Factory Method Pattern)](design-patterns/creational-patterns/03-factory.md)

#####[4. Prototype Pattern](design-patterns/creational-patterns/04-prototype.md)

#####[5. Singleton Pattern](design-patterns/creational-patterns/05-singleton.md)

#**4. Structural Patterns**

**Structural patterns explain how to assemble objects and classes into larger structures while keeping these structures flexible and efficient.**

#####[1. Adapter Structure Pattern](design-patterns/structural-patterns/01-adapter.md)

#####[2. Bridge Structure Pattern](design-patterns/structural-patterns/02-bridge.md)

#####[3. Composite Structure Pattern](design-patterns/structural-patterns/03-composite.md)

#####[4. Decorator Structure Pattern](design-patterns/structural-patterns/04-decorator.md)

#####[5. Facade Structure Pattern](design-patterns/structural-patterns/05-facade.md)

#####[6. Flyweight Structure Pattern](design-patterns/structural-patterns/06-flyweight.md)

#####[7. Proxy Structure Pattern](design-patterns/structural-patterns/07-proxy.md)

#**5. Behavioral Patterns**

#####[1. Chain of responsibility Behavioral Pattern](design-patterns/structural-patterns/01-adapter.md)
#####[2. Command Behavioral Pattern](design-patterns/structural-patterns/02-command.md)
#####[3. Iterator Behavioral Pattern](design-patterns/structural-patterns/03-iterator.md)
#####[4. Mediator Behavioral Pattern](design-patterns/structural-patterns/04-mediator.md)
#####[5. Memento Behavioral Pattern](design-patterns/structural-patterns/05-memento.md)
#####[6. Observer Behavioral Pattern](design-patterns/structural-patterns/06-observer.md)
#####[7. State Behavioral Pattern](design-patterns/structural-patterns/07-state.md)
#####[8. Strategy Behavioral Pattern](design-patterns/structural-patterns/08-strategy.md)
#####[9. Template method Behavioral Pattern](design-patterns/structural-patterns/09-template-method.md)
#####[10. Visitor Behavioral Pattern](design-patterns/structural-patterns/10-visitor.md)

