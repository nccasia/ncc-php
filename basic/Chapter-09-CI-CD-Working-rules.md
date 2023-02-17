# CI, CD - Github action

Continuous integration and continuous delivery

The CI/CD pipeline is one of the best practices for devops teams to implement, for delivering code changes more frequently and reliably

## Standard CI pipeline

With CI, each change in code triggers an automated build-and-test sequence for the given project, providing feedback to the developer(s) who made the change. 

- push the commits
- performs a “build and test.” - build environment image and test (coding convention, unit tests, functional tests) on it
- notifies the team of the integration result. There should generally be four outcomes: failed build, successful build, failed tests, successful tests.
- If there’s a failure, the team fixes the issue ASAP
- When the feature branch is merged to the main branch, they repeat steps 2–6.

## Standard CD pipeline

Continuous Delivery includes infrastructure provisioning and deployment, which may be manual and consist of multiple stages. What’s important is that all these processes are fully automated, with each run fully logged and visible to the entire team.

- deploy on testing/staging environment
- deploy on production environment

## GitHub Actions 

help to Automate, customize, and execute your software development workflows right in your repository with GitHub Actions

https://lab.github.com/githubtraining/github-actions:-hello-world

# Working rules

- Make sure you understand the requirement
- When in doubt - don’t guess! Ask questions!
- Do research for solution and Ask questions!
- First make it work then make it pretty
- Embrace the unknown - Stay curious!
- Discuss with other developer if you change his code
- Keep commitment!
- Always test the code locally before submitting for review
- Write down document as much as possible

# Tips and tricks for a developer

https://code.tutsplus.com/tutorials/3-key-software-principles-you-must-understand--net-25161

https://developer.ibm.com/articles/os-php-7oohabits/

https://www.slideshare.net/rdohms/object-calisthenicstek13

https://github.com/alexeymezenin/laravel-best-practices

## Readability and maintainability: 

- Is the code readable as written?  
- Does it require additional comments, better naming, or general refactoring to be easily understood?  
- Does the code generally conform to the style of coding for the project?
- use code standard (PSR)
- internal review before submitting
- Names are simple and if possible short
- Names are spelled correctly
- No hardcoded constants that could possibly change in the future
- There is no commented out code
- Debugging code is absent
 
 
## Quality and expandability:
 - All variables are in the smallest scope possible
 - There is no dead code (inaccessible at Runtime)
 - No code that can be replaced with library functions
 - Variables are not accidentally used with null values
 - Code is not repeated or duplicated
 - No complex/long boolean expressions
 - No empty blocks of code
 - Ideal data structures are used
 - Catch clauses are fine-grained and catch specific exceptions. Exceptions are not eaten if caught unless explicitly documented otherwise
 - Blocks of code inside loops are as small as possible
 - Code is unit-testable and is covered at least 70%
 - each function contain a (very) brief comment describing functionality, inputs, and outputs
 - Design patterns if used are correctly applied
 - A class should have only a single responsibility
 - Many client-specific interfaces are better than one general-purpose interface
 - Depend upon Abstractions. Do not depend upon concretions

## Tools (see Wordpress plugin)
 - Unittests: php-coveralls
 - phpcs
 - phpstan

# Docker:

1. What is Docker? - basic things like image, container, daemon, host machine, share resource
2. How does Docker work?
3. What are the benefits of using Docker?
4. How to build image, run and stop, inspect container ?
5. Docker-compose
6. Docker Network 