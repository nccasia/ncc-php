# Chapter 02: Necessary Knowledge Base (continue)

1. [PHP Necessary Knowledge Base](#1-php-necessary-knowledge-base) <br>
1-1 [What is PHP](#1-1-what-is-php)<br>
1-2 [Basic PHP syntax](#1-2-basic-php-syntax)<br>
1-3 [Tags in Html](#1-3-tags-in-html)<br>
3. [Popular PHP Extensions](#2-popular-php-extensions)

## 1. PHP Necessary Knowledge Base
### 1-1. What is PHP?
PHP (Personal Home Page) is an open source scripting language commonly used to create web applications running on servers. PHP code can be embedded in an HTML page using the PHP <? Php?> Tag pair.
```html
<!DOCTYPE html>
<html>
<head>
    <title>Embeds the PHP code and the HTML page</title>
</head>
<body>
    <?php
        echo "Hello PHP!";
    ?>
</body>
</html>
```
### 1-2. Basic PHP Syntax
1. The extension to be used is .php
2. PHP code is placed in the snippet `<? Php?>`
3. Place a semicolon at the end of each line of code
4. Run file: php file-name.php

test.php
```
<?php
echo 'Hello world';
```
Run file in terminal and result

![Basic web service](images/run-file-php.png?raw=true)

**How to comment code**

Comment lines are comments to aid in reading and understanding code.

Writing comments code isn't always mandatory, but writing them can help with future review.

There are 3 ways to write comments in PHP code as follows:

- Type "//" at the beginning of the line
- Type "#" at the beginning of the line
- Or wrap the comment between the two signs "/" and "/"

**Declare variable**

When writing software, there are reusable information strings that are saved as variables.

Variables can be used to store almost any type of data, from long text strings to numbers, true-false (Boolean) ...

However, PHP has some predefined variables that cannot be overridden, such as $ GLOBALS, or $ _GET.

For example, we have the following code:
```php
<?php
    $name = ‘NCC’;
    echo $name;
?>
```
Then, the text "NCC" will be displayed on the interface, since it is saved as a string in the variable "$ name", the variable "$ name" can then be changed according to the logic of the application.

There are several rules for defining variables in PHP as follows:

Begin with the dollar character ($)

But characters allowed for variable names include a-z, A-Z, 0-9, and _

Variable names starting with digits 0-9 cannot be named

Japanese can also be used as variable names, but it shouldn't be

Naming variables are not too strict but should be set so that it is clear, easy to understand, and true of the variable nature.

**PHP Data Types**

PHP supports the following data types:
- String
- Integer
- Float (floating point numbers - also called double)
- Boolean
- Array
- Object
- NULL
- Resource

**Operators**

Operators in PHP are symbols that can be used in calculations.
 
 There are arithmetic operators such as addition, subtraction, multiplication, comparison, or operators used for inference ...
 
 For example, we have the following code:
```php
<?php
    $sum = 2 + 3;
    echo “2 + 3 = $sum”;
?>
```

**PHP if...else...elseif Statements**
The "if" snippet is often used to check if the next part has a true (TRUE) value, and will execute the internal code if the above condition is met.
```php
<?php
    $condition = 3;
    if ($condition === 3) {
       echo “Conditions”;
    } else {
       echo “Unsatisfactory”;
    }
?>
```
Thus, the text "Conditions" will be displayed for the value of the variable "$ condition" equal to 3.

The "while" code is used to run the code repeatedly, until the while condition is no longer satisfied.
```php
<?php
    $increment = 1;
    while ($increment <= 5) {
       echo “Run 5 times”;
       $increment++;
    }
?>
```
The text "Run 5 times" will display exactly 5 times on the screen, until the variable "$ increment" is incremented by 1 after 5 loops and the final value after 5 increments are greater than 5.

**Function declaration**

Functions in PHP are groups of code that are grouped and can be executed when the function is called.

For example, we have the following sum function:
```php
<?php
    function sum ($a, $b) {
       return $a + $b; 
    }
?>
```
When calling the function "sum" as follows, we get the sum of 2 numbers is 5 and it is displayed on the interface:
```php
<?php
    echo sum(2, 3);
?>
```
**Others Basic PHP needs to know** 
- PHP Forms: PHP Form Handling, PHP Form Validation, PHP Form Required ...
- PHP Switch
- PHP Loops
- PHP Constants
- PHP Numbers


To learn more about PHP, you can refer to the following link:
[https://www.w3schools.com/php](https://www.w3schools.com/php)

### 1-3. Some base property
**Namespace**

_Dùng để định danh và phân biệt các class trùng tên.
_Namespace nên đặt theo cấu trúc thư mục của file chứa class.
_Namespace phải đặt trên đầu file php chứa class.
_Nạp namespace trên đầu file (dưới khai báo namespace của file đó) bằng cách dùng "use". Sử dụng "as" nếu muốn đổi tên namespace trong file.
```php
<?php

namespace App\Domain\UserManagement\Services;

use Illuminate\Support\Collection;

class UserProfileService
{
```

**Type hint**

Tính năng của php, quy định kiểu tham số truyền vào và kiểu dữ liệu trả về. Bao gồm:
_(Type Declarations) Kiểu tham số truyền vào: class, array, string, integer, float, boolean.
_(Return type declarations) Kiểu dữ liệu trả về: 
```php
    public function test(array $data): array
    {
        // sth code 
    }
```
_Giúp code chặt chẽ + giúp hình dung sơ bộ về tham số và dữ liệu trả ra của hàm

**Access modifier**

(dang viet do)

### 1-4. Popular PHP Extensions

PHP runs on Zend Engine platform. Zend Engine takes care of interpreting PHP code into machine code and executing it.

Zend Engine itself provides a number of libraries available so that PHP can run directly without an external library, but most of those libraries are Text processing libraries. The other PHP libraries are written in the form of extensions, these libraries mainly work with PHP through the Zend Engine. Some of PHP's I/O processing is through external libraries, not core support: for example, DB connection, working with HTTP, image processing ...

Here are the popular PHP extensions that often required in your future work:

- bcMath
- cURL
- mcrypt
- ...



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
    Repository
    
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

# Some popular patterns:

1. Builder - Factory
2. Singleton
3. Repository
4. Decorator
5. Observer
6. Strategy