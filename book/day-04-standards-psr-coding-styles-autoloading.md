# Day 04: Standards PSR, Coding styles, Auto Loading

Each project when executed will use a multitude of libraries, famework, and components.
So in order to easily combine different libraries for the project, the coding should follow a general rule.
In this section we will learn how to code according to the standards recommended by the php community

Table of contents

1. [PSR-0: Auto loading Standard](#psr-0)
2. [PSR-1: Basic Coding Standard](#psr-1)
3. [PSR-2: Coding Style Guide](#psr-2)
4. [PSR-3: Logger Interface](#psr-3)
5. [PSR-4: Autoloader](#psr-4)
6. [PSR-6: Caching Interface](#psr-6)

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

## 2. PSR-1: Basic Coding Standard
**Overview**

1. Files MUST use only <?php and <?= tags.

2. Files MUST use only UTF-8 without BOM for PHP code.

3. Files SHOULD either declare symbols (classes, functions, constants, etc.) or cause side-effects (e.g. generate output, change .ini settings, etc.) but SHOULD NOT do both.

4. Namespaces and classes MUST follow an “autoloading” PSR: [PSR-0, PSR-4].

5. Class names MUST be declared in StudlyCaps.

6. Class constants MUST be declared in all upper case with underscore separators.

7. PHP code MUST use the long <?php ?> tags or the short-echo <?= ?> tags; it MUST NOT use the other tag variations.

8. PHP code MUST use only UTF-8 without BOM.\

9. Namespaces and classes MUST follow an “autoloading” PSR: [PSR-0, PSR-4].

10. The term “class” refers to all classes, interfaces, and traits. Method names MUST be declared in camelCase().

Method names MUST be declared in camelCase.

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

## 4. PSR-3: Logger Interface

1. The LoggerInterface exposes eight methods to write logs to the eight RFC 5424 levels (debug, info, notice, warning, error, critical, alert, emergency).

2. Every method accepts a string as the message, or an object with a __toString() method. Implementors MAY have special handling for the passed objects. If that is not the case, implementors MUST cast it to a string.
   
   The message MAY contain placeholders which implementors MAY replace with values from the context array.
   
   Placeholder names MUST correspond to keys in the context array.
   
   Placeholder names MUST be delimited with a single opening brace { and a single closing brace }. There MUST NOT be any whitespace between the delimiters and the placeholder name.
   
   Placeholder names SHOULD be composed only of the characters A-Z, a-z, 0-9, underscore _, and period .. The use of other characters is reserved for future modifications of the placeholders specification.
   
3. The Psr\Log\AbstractLogger class lets you implement the LoggerInterface very easily by extending it and implementing the generic log method. The other eight methods are forwarding the message and context to it.
   
4. Similarly, using the Psr\Log\LoggerTrait only requires you to implement the generic log method. Note that since traits can not implement interfaces, in this case you still have to implement LoggerInterface.
   
5. The Psr\Log\NullLogger is provided together with the interface. It MAY be used by users of the interface to provide a fall-back “black hole” implementation if no logger is given to them. However, conditional logging may be a better approach if context data creation is expensive.
   
6. The Psr\Log\LoggerAwareInterface only contains a setLogger(LoggerInterface $logger) method and can be used by frameworks to auto-wire arbitrary instances with a logger.
   
7. The Psr\Log\LoggerAwareTrait trait can be used to implement the equivalent interface easily in any class. It gives you access to $this->logger.
   
8. The Psr\Log\LogLevel class holds constants for the eight log levels.

## 5. PSR-4: Autoloader
This PSR describes a specification for autoloading classes from file paths. It is fully interoperable, and can be used in addition to any other autoloading specification, including PSR-0. This PSR also describes where to place files that will be autoloaded according to the specification.
1. The term “class” refers to classes, interfaces, traits, and other similar structures.
2. A fully qualified class name has the following form:

` \<NamespaceName>(\<SubNamespaceNames>)*\<ClassName>`

The fully qualified class name MUST have a top-level namespace name, also known as a “vendor namespace”.

The fully qualified class name MAY have one or more sub-namespace names.

The fully qualified class name MUST have a terminating class name.

Underscores have no special meaning in any portion of the fully qualified class name.

Alphabetic characters in the fully qualified class name MAY be any combination of lower case and upper case.

All class names MUST be referenced in a case-sensitive fashion.
3. When loading a file that corresponds to a fully qualified class name …
A contiguous series of one or more leading namespace and sub-namespace names, not including the leading namespace separator, in the fully qualified class name (a “namespace prefix”) corresponds to at least one “base directory”.

The contiguous sub-namespace names after the “namespace prefix” correspond to a subdirectory within a “base directory”, in which the namespace separators represent directory separators. The subdirectory name MUST match the case of the sub-namespace names.

The terminating class name corresponds to a file name ending in .php. The file name MUST match the case of the terminating class name.
4. Autoloader implementations MUST NOT throw exceptions, MUST NOT raise errors of any level, and SHOULD NOT return a value.

## 6. Caching Interface
Caching is a common way to improve the performance of any project, making caching libraries one of the most common features of many frameworks and libraries. This has lead to a situation where many libraries roll their own caching libraries, with various levels of functionality. These differences are causing developers to have to learn multiple systems which may or may not provide the functionality they need. In addition, the developers of caching libraries themselves face a choice between only supporting a limited number of frameworks or creating a large number of adapter classes.
Implementing libraries MUST support all serializable PHP data types, including:

1. Strings - Character strings of arbitrary size in any PHP-compatible encoding.
2. Integers - All integers of any size supported by PHP, up to 64-bit signed.
3. Floats - All signed floating point values.
4. Boolean - True and False.
5. Null - The actual null value.
6. Arrays - Indexed, associative and multidimensional arrays of arbitrary depth.
7. Object - Any object that supports lossless serialization and deserialization such that $o == unserialize(serialize($o)). Objects MAY leverage PHP’s Serializable interface, __sleep() or __wakeup() magic methods, or similar language functionality if appropriate.
8. All data passed into the Implementing Library MUST be returned exactly as passed. That includes the variable type. That is, it is an error to return (string) 5 if (int) 5 was the value saved. Implementing Libraries MAY use PHP’s serialize()/unserialize() functions internally but are not required to do so. Compatibility with them is simply used as a baseline for acceptable object values.

If it is not possible to return the exact saved value for any reason, implementing libraries MUST respond with a cache miss rather than corrupted data.

The Pool represents a collection of items in a caching system. The pool is a logical Repository of all items it contains. All cacheable items are retrieved from the Pool as an Item object, and all interaction with the whole universe of cached objects happens through the Pool.

While caching is often an important part of application performance, it should never be a critical part of application functionality. Thus, an error in a cache system SHOULD NOT result in application failure. For that reason, Implementing Libraries MUST NOT throw exceptions other than those defined by the interface, and SHOULD trap any errors or exceptions triggered by an underlying data store and not allow them to bubble.

CacheItemInterface defines an item inside a cache system. Each Item object MUST be associated with a specific key, which can be set according to the implementing system and is typically passed by the Cache\CacheItemPoolInterface object.

The Cache\CacheItemInterface object encapsulates the storage and retrieval of cache items. Each Cache\CacheItemInterface is generated by a Cache\CacheItemPoolInterface object, which is responsible for any required setup as well as associating the object with a unique Key. Cache\CacheItemInterface objects MUST be able to store and retrieve any type of PHP value defined in the Data section of this document.

Calling Libraries MUST NOT instantiate Item objects themselves. They may only be requested from a Pool object via the getItem() method. Calling Libraries SHOULD NOT assume that an Item created by one Implementing Library is compatible with a Pool from another Implementing Library.