# Chapter 06: Unit Test

In software testing there are 4 levels of testing:
1. Unit test
2. Integration test
3. System test
4. Acceptance test

Unit test is the smallest test level in the software testing process. Unit test will test the smallest units in source code such as method, class, module ...
Unit test checks the source code of the programs, individual functions working properly or not.

Unit tests are performed by the programmer.

**1. The basic concepts in Unit test**

**1.1 Assertion**

The assertion is a statement that describes the test to be performed.
For example: AreEqual (), IsTrue (), IsNotNull () ...
Each UT consists of multiple assertions that check for the output, the integrity of the outlier errors, and other complex problems like:
- Existence of an object
- Boundary condition: Whether the values ​​exceed the limit or not
- Order of execution of data streams

**1.2. Test Point**

Test Point is the smallest test unit, containing only one assertion to confirm the correctness of a certain code detail.
Any project member can write a test point.
Test Case: A set of test points that test a particular functional set, for example, the entire period a user enters data until the information is entered into the database.
In special and urgent cases, test cases may not be needed.

**1.3. Test Suite**

Is a set of test cases defined for each module or subsystem.

**1.4. Regression Testing**

An automated test method using special software. The same test data is the same but is automatically repeated many times to prevent old errors from reoccurring.

**1.5. Production Code**

The main part of the application code is transferred to the customer.

**1.6. Unit Testing Code**

The extra code for testing the main application code is not passed on to the customer.

**2. Unit test life cycle**

Unit test has 3 basic states:

- Fail (The color of the status is usually red)
- Ignore (The color of the state is usually yellow)
- Pass (The color of the status is usually green)

**3. How to write effective unit tests**
- Please make each test independent from all others
- Don't do unnecessary assertions
- Test only one unit of code at a time
- Emulate all external services and states
- Avoid unnecessary prerequisites

**4. The procedure of writing 1 Unit test**
- Set the necessary conditions: Initialize objects, identify necessary resources, build dummy data ...
- Call the methods to check
- Check for the correct functioning of the methods
- Clean up resources after the test is finished

**6. Install PHP Unit**
- We will use composer to install the PHP unit by adding the following code to the "composer.json" file.

- If you do not know about composer and autoload, you can see this content in [Chapter 04: Standards PSR, Coding styles, Auto Loading] (./ book / Chapter-04-standards-psr-coding-styles-autoloading.md)
```
{
    "require-dev": {
        "phpunit / phpunit": "^ 6.2" // version PHPUnit you want to use
    },
    "autoload": {
        "psr-4": {
            "App \\": "app /"
        },
    },
    "autoload-dev": {
        "psr-4": {
            "Tests \\": "tests /"
        }
    },
}
```
**- Setting**

```composer require --dev phpunit / phpunit ^ 6.2```

Since we are using Composer, we will need the project structure a bit for it to work with an autoloader. Unit tests will be written to the tests directory with the namespace Tests.
- Next, run the command
`` composer dump-autoload ''
- Start writing 1 Unit test first

1.Create a "./tests/ExampleTest.php" file with the following content
```php
<?php
   
   namespace Tests;
   
   use PHPUnit\Framework\TestCase;
   
   class ExampleTest extends TestCase
   {
       public function testTrueIsTrue ()
       {
           $ncc = true;
           $this-> assertTrue ($ncc);
       }
   }
```
2. To run PHPUnit we use the following command
``
./vendor/bin/phpunit
``
For better understanding, you can refer to the following documents:

[https://phpunit.de/documentation.html](https://phpunit.de/documentation.html)

 