- [Overview](#overview)
- [Laravel framework](#laravel-framework)
  - [1. About Laravel](#1-about-laravel)
  - [2. Install laravel](#2-install-laravel)
  - [3. The structure of Laravel](#3-the-structure-of-laravel)
  - [4. Example projects in laravel](#4-example-projects-in-laravel)


# Overview

A web framework (WF) or web application framework (WAF) is a software framework that is designed to support the development of web applications including web services, web resources, and web APIs. Web frameworks provide a standard way to build and deploy web applications on the World Wide Web.

It is a collection of packages or modules which allow developers to write Web applications (see WebApplications) or services without having to handle such low-level details as protocols, sockets or process/thread management.

Generally, frameworks provide support for a number of activities such as
- URL routing and interpreting requests (getting form parameters, handling cookies and sessions, authentication)
- producing responses (presenting data as HTML or in other formats)
- integrating with some frontend javascript technology (AJAX, angular, reactjs, etc)
- storing data persistently, ORM, caching and so on
- ability to run and manage migrations
- basic security features such as XSS and CRSF prevention
- support for feature or unit-testing
- Inbuilt development web server
- logging
- external modules, libraries management

# Laravel framework

## 1. About Laravel

Laravel is a free and open source PHP Framework, developed by Taylor Otwell 
and targeted to support the development of web applications in a model-view-controller (MVC) architecture.

Laravel includes an easy-to-understand syntax, Many different utilities support deployment into application maintenance.

## 2. Install laravel

- [Laravel install](https://laravel.com/docs/8.x/installation)

## 3. The structure of Laravel

- **app:** Contains directories, php files, libraries, models.

    **- Console:** Contains files that define the commands on artisan.
    
    **- Exception:** Contains file management and error navigation.
    
    **- Http** 
    
        - Controller: Contains the controllers of the project.
        - Middleware: Contains file filtering and blocking requests.
        - Kernel.php: Contains file filtering and blocking requests.
        
    **- Providers:** The providers do the job binding vào service container.
    
    **- User.php:** This is the User model that Laravel defines itself for us.
    
**- bootstrap:** Contains system navigation file.

**- config:** Contains all Laravel configuration files.

**- database:** Contains the file directories on the database.

    - migrations: Contains files that define, initialize and edit tables.
    - seeds: Contains insert data definition files into the database.
    - factory: Contains files that define data table columns to create virtual data.
    
**- public:** Contains css, js, image files.

    - index.php: This is the root file of Laravel.
    
**- resources:** Contains views, language (language) of the project.

**- routes:** Contains the files that define the routers, handling router navigation including: **web, api**

**- storage:** Contains system files cache, session, ...

**- tests:** Contains test files

**- vendor:** Contains the packages laravel requires.

**- .env:** Is the laravel main configuration file such as key app, database.

**- .env.example:** Laravel template configuration file, used to generate .env file

**- composer.json:** composer's file.

**- composer.lock:** composer lock file.

**- package:** The nodejs configuration file (containing the packages needed for projects).

**- phpunit.xml:** The xml file of phpunit used for testing project.

**- server.php:** Is the file for artisan to point to creating the server when typing the command _**php artisan serve**_.

**- artisan:** Laravel command executable file.


## 4. Example projects in laravel

https://github.com/chiraggude/awesome-laravel

https://github.com/munafio/chatify

https://github.com/z-song/laravel-admin