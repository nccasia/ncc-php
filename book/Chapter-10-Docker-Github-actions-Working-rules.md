# Docker

# CI, CD - Github action

# Working rules

- Make sure you understand the requirement
- First make it work then make it pretty
- Embrace the unknown - Stay curious!
- When in doubt - don’t guess!
- Discuss with other developer if you change his code
- Do research for solution and ask questions
- Keep commitment!
- Write down document as much as possible

# Tips and tricks for a developer

https://code.tutsplus.com/tutorials/3-key-software-principles-you-must-understand--net-25161

https://developer.ibm.com/articles/os-php-7oohabits/

https://www.slideshare.net/rdohms/object-calisthenicstek13

https://github.com/alexeymezenin/laravel-best-practices

## Readability and maintainability: Is the code readable as written?  Does it require additional comments, better naming, or general refactoring to be easily understood?  Does the code generally conform to the style of coding for the project?
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

