# Chapter 04: Standards PSR, Coding styles, Auto Loading

Each project when executed will use a multitude of libraries, frameworks, and components.
So in order to easily combine different libraries for the project, the coding should follow a general rule.
In this section we will learn how to code according to the standards recommended by the PHP community

Table of contents

- [Standards PSR, Coding styles, Auto Loading](#standards-psr-coding-styles-auto-loading)
  - [1. PSR-0: Auto loading Standard](#1-psr-0-auto-loading-standard)
  - [2. PSR-1: Basic Coding Standard](#2-psr-1-basic-coding-standard)
  - [3. PSR-2: Coding Style Guide](#3-psr-2-coding-style-guide)
  - [4. PSR-4: Autoloader](#4-psr-4-autoloader)
- [How to setup style configuration on PhpStorm](#how-to-setup-style-configuration-on-phpstorm)
- [Composer](#composer)

---

**Standards PSR**
PSR(PHP Standards Recommendation) - these are documents that lay out how the PHP community has agreed things will be done.
The standards are developed by the FIG (Framework Interoperability Group), which draws members from all the major frameworks and tools built in PHP. Since they have been very widely adopted around the PHP world
## 1. PSR-0: Auto loading Standard
**Mandatory**
1. A fully-qualified namespace and class must have the following structure \<Vendor Name>\(<Namespace>\)*<Class Name>

2. Each namespace must have a top-level namespace (“Vendor Name”).

3. Each namespace can have as many sub-namespaces as it wishes.

4. Each namespace separator is converted to a DIRECTORY_SEPARATOR when loading from the file system.

5. Each _ character in the CLASS NAME is converted to a DIRECTORY_SEPARATOR. The _ character has no special meaning in the namespace.

6. The fully-qualified namespace and class are suffixed with .php when loading from the file system.

7. Alphabetic characters in vendor names, namespaces, and class names may be of any combination of lower case and upper case.

8. Underscores in Namespaces and Class Names

\namespace\package\Class_Name => /path/to/project/lib/vendor/namespace/package/Class/Name.php
\namespace\package_name\Class_Name => /path/to/project/lib/vendor/namespace/package_name/Class/Name.php

The standards we set here should be the lowest common denominator for painless autoloader interoperability. You can test that you are following these standards by utilizing this sample SplClassLoader implementation which is able to load PHP 5.3 classes.

For better understanding, you can refer to the following documents:
[https://www.php-fig.org/psr/psr-0/](https://www.php-fig.org/psr/psr-0/)

## 2. PSR-1: Basic Coding Standard
**Overview**

1. Files MUST use only <?php and <?= tags.

2. Files MUST use only UTF-8 without BOM for PHP code.

3. Files SHOULD either declare symbols (classes, functions, constants, etc.) or cause side-effects (e.g. generate output, change .ini settings, etc.) but SHOULD NOT do both.

4. Namespaces and classes MUST follow an “autoloading” PSR: [PSR-0, PSR-4].

5. Class names MUST be declared in StudlyCaps.

6. Class constants MUST be declared in all upper case with underscore separators.

7. This guide intentionally avoids any recommendation regarding the use of $StudlyCaps, $camelCase, or $under_score property names.
   
   Whatever naming convention is used SHOULD be applied consistently within a reasonable scope. That scope may be vendor-level, package-level, class-level, or method-level. 

8. Method names MUST be declared in camelCase().

For better understanding, you can refer to the following documents:
[https://www.php-fig.org/psr/psr-1/](https://www.php-fig.org/psr/psr-1/)

## 3. PSR-2: Coding Style Guide
This guide extends and expands on PSR-1, the basic coding standard.
1. Code MUST follow a “coding style guide” PSR [PSR-1].

2. Code MUST use 4 spaces for indenting, not tabs.

3. There MUST NOT be a hard limit on line length; the soft limit MUST be 120 characters; lines SHOULD be 80 characters or less.

4. There MUST be one blank line after the namespace declaration, and there MUST be one blank line after the block of use declarations.

5. Opening braces for classes MUST go on the next line, and closing braces MUST go on the next line after the body.

6. Opening braces for methods MUST go on the next line, and closing braces MUST go on the next line after the body.

7. Visibility MUST be declared on all properties and methods; abstract and final MUST be declared before the visibility; static MUST be declared after the visibility.

8. Control structure keywords MUST have one space after them; method and function calls MUST NOT.

9. Opening braces for control structures MUST go on the same line, and closing braces MUST go on the next line after the body.

10. Opening parentheses for control structures MUST NOT have a space after them, and closing parentheses for control structures MUST NOT have a space before.

For better understanding, you can refer to the following documents:
[https://www.php-fig.org/psr/psr-2/](https://www.php-fig.org/psr/psr-2/)

## 4. PSR-4: Autoloader
This PSR describes a specification for autoloading classes from file paths. It is fully interoperable, and can be used in addition to any other autoloading specification, including PSR-0. This PSR also describes where to place files that will be autoloaded according to the specification.
- The term “class” refers to classes, interfaces, traits, and other similar structures.
- A fully qualified class name has the following form:

` \<NamespaceName>(\<SubNamespaceNames>)*\<ClassName>`

The fully qualified class name MUST have a top-level namespace name, also known as a “vendor namespace”.

The fully qualified class name MAY have one or more sub-namespace names.

The fully qualified class name MUST have a terminating class name.

Underscores have no special meaning in any portion of the fully qualified class name.

Alphabetic characters in the fully qualified class name MAY be any combination of lower case and upper case.

All class names MUST be referenced in a case-sensitive fashion.
- When loading a file that corresponds to a fully qualified class name …
A contiguous series of one or more leading namespace and sub-namespace names, not including the leading namespace separator, in the fully qualified class name (a “namespace prefix”) corresponds to at least one “base directory”.

The contiguous sub-namespace names after the “namespace prefix” correspond to a subdirectory within a “base directory”, in which the namespace separators represent directory separators. The subdirectory name MUST match the case of the sub-namespace names.

The terminating class name corresponds to a file name ending in .php. The file name MUST match the case of the terminating class name.
- Autoloader implementations MUST NOT throw exceptions, MUST NOT raise errors of any level, and SHOULD NOT return a value.

For better understanding, you can refer to the following documents:
[https://www.php-fig.org/psr/psr-2/](https://www.php-fig.org/psr/psr-2/)

There are also other standards, For better understanding, you can refer to the following documents:
[https://www.php-fig.org/psr/](https://www.php-fig.org/psr/)

# How to setup style configuration on PhpStorm
1. In the Settings/Preferences dialog Ctrl+Alt+S, go to Editor | Code Style and open the page of your programming language.

2. Click Set From in the upper-right corner.

3. The link is shown for those languages only, where defining settings on the base of other languages is applicable.

4. From the list that appears, select the language to copy the code style from.

![Alt text](images/copyCodeStyle.png?raw=true "CodeStyle")

**Format code in PhpStorm Editor**

We highlight the code to be formatted. Then simultaneously press 3 keys "Crtl + Alt + L"

# Composer
Composer is a dependency manager for PHP (similar to Bundler for Ruby apps). Composer allows developers to specify project dependencies in a composer.json file and then Composer automatically handles the rest.

Composer makes it easier to keep vendor libraries out of your repo, meaning that only application code goes in the git repository. It also makes maintaining the latest versions of all required libraries easier because you can simply run composer update to get the latest compatible packages.

**Installation Composer**
This is the easiest way to get Composer set up on your machine.

Download and run [Composer-Setup.exe](https://getcomposer.org/Composer-Setup.exe). It will install the latest Composer version and set up your PATH so that you can call composer from any directory in your command line.

Test usage with a new terminal:
```
C:\Users\username>composer -V
Composer version 1.0.0 2016-01-10 20:34:53
```
Now that you've installed Composer, you are ready to use it!

1. Create your composer.json file to declare your dependencies.

2. The composer.json file specifies required packages.

3. Run composer install (on your local machine) to install the required packages and generate a composer.lock file.
You can even add your own code to the autoloader by adding an autoload field to composer.json
```
{
    "autoload": {
        "psr-4": {"Ncc\\": "src/"}
    }
}
```

Composer will register a PSR-4 autoloader for the Ncc namespace.

You define a mapping from namespaces to directories. The src directory would be in your project root, on the same level as vendor directory is. An example filename would be src/Foo.php containing an Ncc\Foo class.

# PHPStan vs PHP CodeSniffer

What is PHPStan? PHP Static Analysis Tool - discover bugs in your code without running it!. It focuses on finding errors in your code without actually running it. It catches whole classes of bugs even before you write tests for the code. It moves PHP closer to compiled languages in the sense that the correctness of each line of the code can be checked before you run the actual line.

What is PHP CodeSniffer? A library that detects PHP, CSS and JS coding standard violations. It tokenizes PHP, JavaScript and CSS files and detects violations of a defined set of coding standards. It is an essential development tool that ensures your code remains clean and consistent.

PHPStan and PHP CodeSniffer can be primarily classified as "Code Review" tools.

Some of the features offered by PHPStan are:

 - Static Analysis Tool
 - Focuses on finding errors in your code without actually running it
 - Extensible

On the other hand, PHP CodeSniffer provides the following key features:

 - Code Sniffing
 - Coding Standard Checking
 - Coding Standard Fixing
 
 ## Setup & Run PHPStan - PHP Static Analysis Tool
 
 **1. Make sure installed phpstan/phpstan in vendor by composer**
 
 `composer require "phpstan/phpstan"`
 
 **2. Make sure installed nunomaduro/larastan in vendor by composer**
 
 `composer require "nunomaduro/larastan"`
 
 Run it with level 5 and see result:
 
 `vendor\bin\phpstan analyse . -c phpstan.neon`
 
 phpstan.neon sample file
 
 ```
includes:
    - ./vendor/nunomaduro/larastan/extension.neon

parameters:
    level: 5
    paths:
        - app

    excludes_analyse:
        - vendor
        - storage
        - tests

    bootstrapFiles:

    scanFiles:

    ignoreErrors:
```
 
 Note: Errors from Framework
 
## Setup & Run code sniffer for flowfact-connector
 
 **1. Make sure installed code sniffer in vendor by composer**
 
 `composer require "squizlabs/php_codesniffer=*"`
 
 **2. Make sure installed PHPCompatibility code standard**
 
 `composer require "phpcompatibility/php-compatibility"`
 
 **3. Install php-compatibility into phpcs and used instead like code standard**
 
 `vendor\bin\phpcs --config-set installed_paths vendor\phpcompatibility\php-compatibility`
 
 **Run it with php version 7.4**
 
 `vendor\bin\phpcs -p . --standard=PHPCompatibility --runtime-set testVersion 7.4 --ignore="vendor, storage, *.js,*.min.css"`
