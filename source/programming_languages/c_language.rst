##########################
The C programming language
##########################

This is a personal C documentation with essential informations.

It is meant to be used by someone who is already familiar with the language.

It is based on `The GNU C Reference Manual <https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html>`_.


****************
Lexical Elements
****************

Identifiers
===========

Identifiers are sequences of characters used for naming variables, functions, new data types, and preprocessor macros.

They can contain :

- letters
- decimal digits
- the underscore character '_'

The first character of an identifier cannot be a digit.


Keywords
========

``auto``
    [Description of auto]

``break``
    Breaks out of the current loop/switch.

``case``
    A case that will be checked in a switch statement.

``char``
    Defines a character variable.

``const``
    Defines a constant variable.

``continue``
    Skips the current iteration in a loop.

``default``
    Defines the code to execute if no case was matched in the switch statement.

``do``
    Defines the code to execute while a condition is met. It is different of 'while' as the code will be executed at least once.

``double``
    Defines a double precision number variable.

``else``
    Defines the code to execute if the condition of the precedent 'if' statement is false.

``enum``
    Defines a group of constants.

``extern``
    Declare a variable that is defined in another file.

``float``
    Defines a single precision number variable.

``for``
    Defines the condition of a loop using a starting value, an end value and a step operation.

``goto``
    Jumps to a labeled code section.

``if``
    Checks if the given condition is true.

``int``
    Defines a integer variable.

``long``
    Increases the range and size of values a variable can store.

``register``
    Declare a variable that must be stored inside of a register instead of the memory.

``restrict``
    Declare a pointer that is the only one used to access its variable. The compiler can then optimize its use since no other pointers will be used to access this variable.

``return``
    Ends the execution of a function and returns a value.

``short``
    [Description of auto]

``signed``
    Declare a variable that can store positive and negative values.

``sizeof``
    Gets the memory size of the given data type.

``static``
    Declare a variable which value will be shared across function calls.

``struct``
    Defines a custom data structure that groups multiple variables.

``switch``
    Evaluate the value of a variable and compare it to the given case statements.

``typedef``
    Provides a new name to an existing data type.

``union``
    Defines a custom data structure that groups multiple variables that are stored in the same memory location. Meaning that only one of the variables can be assigned at any given time.

``unsigned``
    Declare a variable that can only store positive values.

``void``
    Defines a function that returns nothing or take no argument. Defines a generic data pointer.

``volatile``
    Defines a variable that the compiler should not optimize.

``while``
    Defines code that will be executed while the given condition is met.


Constants
=========

Integer Constants
-----------------

Integers constants can be represented in different ways :

Hexadecimal
    Starts with 0x or 0X

Octal
    Starts with a 0

Decimal
    Any other sequence of digits

These constants can also be set to specific data types by appending one or more of the following characters to the integer :

- u or U for unsigned
- l or L for long


Character Constants
-------------------

Character constants are usually a single character enclosed within single quotation marks.

A character constant is of type int by default.

There are several “escape sequences” :

``\\``
    Backslash character.

``\?``
    Question mark character.

``\'``
    Single quotation mark.

``\"``
    Double quotation mark.

``\a``
    Audible alert.

``\b``
    Backspace character.

``\f``
    Form feed.

``\n``
    Newline character.

``\r``
    Carriage return.

``\t``
    Horizontal tab.

``\v``
    Vertical tab.

``\o, \oo, \ooo``
    Octal number.

``\xh, \xhh, \xhhh, ...``
    Hexadecimal number.

Octal and Hexadecimal numbers are converted to the character of their ASCII value.


Real Number Constants
---------------------

A real number constant is a value that represents a fractional (floating point) number.

It is composed of :

- The integer part : 0 or more digits
- A decimap point
- The fractional part : 0 or more digits.
- (Optional) e or E
- (Optional) The exponent part : 1 or more digits

Either the integer part or the fractional part may be omitted, but not both.


These constants can also be set to specific data types by appending one or more of the following characters to the integer :

- f or F for float
- l or L for long double
- none for double


String Constants
----------------

.. TODO


Operators
=========

An operator is a special token that performs an operation, such as addition or subtraction, on either one, two, or three operands.

Full coverage of operators can be found in `Expressions and Operators`_.


Separators
==========

A separator separates tokens. `White Space`_ is a separator, but it is not a token.

The other separators are all single-character tokens themselves:

- ``(``
- ``)``
- ``[``
- ``]``
- ``{``
- ``}``
- ``;``
- ``,``
- ``.``
- ``:``


White Space
===========

**********
Data Types
**********

Syntax
======

.. code-block:: c

    type variable_name = value;


Data types
==========

.. code-block:: c

    bool is_valid = true;

    char letter = 'a'; // 8 bits

    short small = 3; // 16 bits
    int number = 16; // 16 bits
    long big = 128; // 32 bits
    long long bigger = 1024; // 64 bits

    float price = 9.99; // 32 bits
    double pi = 3.1415926535; // 64 bits

.. code-block:: c

    enum Day {}

*************************
Expressions and Operators
*************************

**********
Statements
**********

*********
Functions
*********

***************************
Program Structure and Scope
***************************
