# Chapter 01: Necessary Knowledge Base

These are the basic knowledge required to be able to get started with PHP.
This series focuses on PHP, so this knowledge only stops at the level of listing and introduction.

Table of contents

1. [Basic Html](#1-basic-html)
2. [Css](#2-css)
3. [PHP Necessary Knowledge Base](#3-php-necessary-knowledge-base)
4. [Popular PHP Extensions](#4-popular-php-extensions)

---

![Basic web service](images/basic_web_service.png?raw=true "Css")

## 1. Basic Html
### 1.1 What is Html?
HTML stands for HyperText Markup Language (translated as HyperText Markup Language) used to create a web page.
A website can contain many pages and each page is referred to as an HTML document.
### 1.2 Html Syntax Structure
Below is an example of one of the simplest examples of an HTML document.
```html
<!DOCTYPE html>
<html>
<head>
<title>This is Title Tag</title>
</head>
<body>
<h1>This is H1 Tag</h1>
<p>This is P Tag</p>
</body>
</html>
```
**Tags in HTML - Tags in HTML**

HTML is tag language and uses different tags to format the content. These tags are contained within two parentheses <tag name>.
Except for a few tags, most tags have their corresponding closing tags. For example, the tag `<html>` has a close tag of `</html>`, and the `<body>` tag has a corresponding close tag of `</body>`...
	
Think that if the website is a complete body, the HTML is the skeleton of that body.

Website has two main types:

- Static website - Is a website that does not communicate with the web server to send and receive data but only the data is pre-declared by HTML and the browser to read.
- Dynamic website - A website that will communicate with a server to send and receive data, the data will be sent out to the user using HTML text and the browser will display it. 
In order for a website to communicate with the web server, it will use some server-side programming languages such as PHP, ASP.NET, Ruby, .. to perform. For example, a website made of WordPress is a dynamic website.

**Basic html tags need to know:**
- HTML Headings
- HTML Paragraphs
- HTML Attributes
- HTML Colors
- HTML Links
- HTML Images
- HTML Tables
- HTML Lists
- HTML JavaScript
- HTML Responsive Web Design
- HTML Forms

To learn more about the other tags and their meanings, you can find out at the following link:

[https://www.w3schools.com/html](https://www.w3schools.com/html/)

## 2. Css
### 2.1 What is Css?
CSS is a language to create style for the website - Cascading Style Sheet language. It is used to style and style elements written in markup language, such as HTML. It can control the formatting of multiple web pages at the same time to save the effort of web writers.
It distinguishes the appearance of the web page from the main content of the page by controlling the layout, color, and font.
### 2.2 Css syntax structure
Here is an example of one of the simplest Css templates.
```css
body {
    background-color: black;
    color: #fff;
}
```

The above Css will define all the html elements in the body tag, the background image will be black and the text is white.

**Embed CSS in HTML**

**Inline: CSS code written in the style attribute of the HTML element**
```html
<p style="color:white; background-color:red;"></p>
```
**Internal: the CSS code in the HTML document itself, inside the tag block `<style>`**
```html
<html>
   <head> 
      <link rel="stylesheet" href="demo.css">
   </head>
</html>
```
**External: CSS code in a separate file then loaded into HTML with the element `<link>`**
```html
<html>
   <head>
      <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" />
   </head>
   <body>
      <p class="display-1 text-success">Hello CSS</p>
   </body>
</html>

```
**Css specific syntax**

![Alt text](images/css-declaration-small.png?raw=true "Css")
1. Selector
The HTML element name at the beginning of the rule set. It selects the styled element (s) (p element in this case). To style another element, simply change the selector.
Declaration
A single rule like: color: red; specifies which element properties you want to style.

2. Properties
Ways you can style an HTML element.
(In this case, color is an attribute of the `<p>` element.) In CSS, you choose which property you want to affect in your rule.

3. Attribute value
To the right of the property after the colon (:), we have the property value, which chooses one out of as many possible occurrences for a particular property (color has a lot of values ​​beyond red).

**Basic CSS need to know:**
- CSS Colors
- CSS Backgrounds
- CSS Borders
- CSS Margins
- CSS Padding
- CSS Height and Width
- CSS Dropdowns
- CSS Forms
- CSS Transitions
- CSS Animation
- CSS Buttons
- CSS Pagination
- CSS Responsive

To learn more about other properties of CSS, learn more at the following link:

[https://www.w3schools.com/css](https://www.w3schools.com/css/)

To write CSS in a more professional, fast and coherent way, we will write css using **SASS or SCSS.**

**The first concept to know is CSS Preprocessors.**

CSS Preprocessors is a scripting language that extends CSS and is compiled into CSS syntax to help you write CSS faster and have a clearer structure.
CSS Preprocessor can save you time writing CSS, easy maintenance and development of CSS.

**Basic SASS / SCSS need to know:**
- Sass Variables
- Sass @import
- Sass @mixin
- Sass Functions

To learn more about other properties of CSS, learn more at the following link:

[https://www.w3schools.com/sass/](https://www.w3schools.com/sass/)

## 3. PHP Necessary Knowledge Base
### 3.1 What is PHP?
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
### 3.2  Basic PHP Syntax
1. The extension to be used is .php
2. PHP code is placed in the snippet `<? Php?>`
3. Place a semicolon at the end of each line of code

```html
<?php
echo ‘Hello World’;
# This is comment
?>
```
**How to comment code**

Comment lines are comments to aid in reading and understanding code.

Writing comments code isn't always mandatory, but writing them can help with future review.

There are 3 ways to write comments in PHP code as follows:

- Type "//" at the beginning of the line
- Type "#" at the beginning of the line
- Or wrap the comment between the two signs "/" and "/"

**Basic Syntax** 

**Declare variable**

When writing software, there are reusable information strings that are saved as variables.

Variables can be used to store almost any type of data, from long text strings to numbers, true-false (Boolean) ...

However, PHP has some predefined variables that cannot be overridden, such as $ GLOBALS, or $ _GET.

For example we have the following code:
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
 
 For example we have the following code:
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

For example we have the following sum function:
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
**Others Basic PHP need to know** 
- PHP Forms: PHP Form Handling, PHP Form Validation, PHP Form Required ...
- PHP Switch
- PHP Loops
- PHP Constants
- PHP Numbers


To learn more about PHP, you can refer to the following link:
[https://www.w3schools.com/php](https://www.w3schools.com/php)

## Magic methods, trait, reflection

## 4. Popular PHP Extensions
### 4.1 PHP Extensions là gì?

PHP runs on Zend Engine platform. Zend Engine takes care of interpreting PHP code into machine code and executing it.
All resource management of PHP is handled by Zend Engine.
Zend Engine itself provides a number of libraries available so that PHP can run directly without an external library, but most of those libraries are Text processing libraries. The other PHP libraries are written in the form of extensions, these libraries mainly work with PHP through the Zend Engine. Some of PHP's I / O processing is through external libraries, not core support: for example, DB connection, working with HTTP, image processing ...

Here are the basic PHP extensions and research documentation:
https://en.wikipedia.org/wiki/List_of_PHP_extensions

- bcMath
- cURL
- mcrypt
- ...



