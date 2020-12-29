## OOP
```
class A
{
    public function foo()
    {
        echo "A class";
    }
    
    protected function bar()
    {
        $this->foo();
    }
}

class B extends A
{
    public function foo()
    {
        echo "B class";
    }
}

$b = new B();
$b->foo();
```

## Late Static Bindings:

PHP 5.3.0 -> keyword "static"

reference the called class in a context of static inheritance.

```
<?php
class A {
    public static function who() {
        echo __CLASS__;
    }
    public static function test() {
        self::who(); // A::who is called
        static::who(); // Here comes Late Static Bindings B::who is called
    }
}

class B extends A {
    public static function who() {
        echo __CLASS__;
    }
}

B::test();
?>
```
self is "bound" at compile time, statically. That means when the code is compiled, it is decided what self refers to. static is resolved at run time, i.e. when the code is executed. That's late static binding. And that's the difference.

## Algorithms

Array numbers from 1 to 100. Write a script to encrease each number 5

Array numbers from 1 to 100, suffle and delete 1 of them. Find the missing number in 1 iteration.

Array abitrarry numbers, that each number appreares twice. Suffle and delete 1 of them. Find the deleted number in 1 iteration.

## PSR

Do you follow any coding standard ?

0,4: autoloading
1,2: style guide

## How to call grandparent method
http://stackoverflow.com/questions/12850802/how-to-call-grandparent-method-without-getting-e-strict-error

## Composer

## Array iteration

$a = range(1,10);

foreach ($a as $k => $v) {
    var_dump($v);

    if (isset($a[$k])) {
        echo "Hello";
        unset($a[$k]);
    }
}
http://stackoverflow.com/questions/10057671/how-does-foreach-actually-work
--> can create a tech talk
https://nikic.github.io/2011/11/11/PHP-Internals-When-does-foreach-copy.html
http://schlueters.de/blog/archives/141-References-and-foreach.html

## In PHP arrays are assigned by copy, while objects are assigned by reference

## Gia lap class trong js: class chinh la mot ham duoc xem nhu constructor

## Versions changes:

PHP 5.3: namespace, closure, late static binding

## https://github.com/phpmentoring/resources-php


## https://github.com/danrevah/php-exercises

the curry exercises is good

## https://github.com/Kami/practical-php-testing-exercise-solutions
