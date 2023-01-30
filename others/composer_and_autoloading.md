## Composer and autoloading

### Class loading

```
requires /path/to/classfile
```

### Composer and Autoloading

Composer uses PSR-4 autoloading to automatically include the required files in a PHP project based on the namespaces used in the code. When you install a package using Composer, it adds the package's autoloading rules to your project's composer.json file.

When your PHP code references a class or namespace that hasn't been included yet, Composer's autoloader checks the composer.json file to see if it has a rule for that namespace. If it finds a match, it includes the required file automatically.

This makes it easy to use third-party packages and components in your project without having to manually include each file. Simply run composer install to install all dependencies and you are ready to go.

### Composer and Preloading

Composer preloads classes by generating a single optimized autoload file that includes all required dependencies for a project. This is done through the composer dump-autoload command, which generates a single optimized autoloader file.

```
 /vendor/autoload.php
```

This file is then included in the project's bootstrap process, allowing all required classes to be loaded quickly and efficiently. By preloading all the classes, Composer reduces the overhead of autoloading and improves the performance of your application.

Additionally, Composer also supports classmap autoloading, where it generates a map of all the classes in a project and their file paths, allowing for fast and direct access to classes without the need for a more complex autoloading mechanism.

Both of these autoloading techniques make it easier to include and manage dependencies in a project, and allow for a faster and more efficient bootstrap process.

Exercise:

```
spl_autoload_register
```