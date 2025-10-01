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

``__Bool``
    Defines a boolean variable. It is the primary type of the ``bool`` alias.

``_Complex``
    Defines a complex number variable.

``_Imaginary``
    Defines an imaginary number variable.

``auto``
    [Description of auto]. Auto is used by default for variables so there is no need to use it.

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

``inline``
    Declare a function that must be optimized for time performance.

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

A constant is a literal numeric or character value.

All constants are of a particular data type; you can use type casting to explicitly specify the type of a constant, or let the compiler use the default type based on the value of the constant. 


Integer Constants
-----------------

An integer constant is a sequence of digits, with an optional prefix to denote a number base.

Hexadecimal
    Starts with 0x or 0X

Octal
    Starts with a 0

Decimal
    Any other sequence of digits

You can force an integer constant to be of a long and/or unsigned integer type by appending a sequence of one or more letters to the end of the constant:

``u`` or ``U``
    Unsigned integer type.

``l`` or ``L``
    Long integer type.


Character Constants
-------------------

A character constant is usually a single character enclosed within single quotation marks.

A character constant is of type int by default. 

There are several “escape sequences” that you can use :

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

``f`` or ``F``
    Float

``l`` or ``L``
    Long double

Nothing
    Double


String Constants
----------------

A string constant is a sequence of zero or more characters, digits, and escape sequences enclosed within double quotation marks.

A string constant is of type “array of characters”.

All string constants contain a null termination character ``\0`` as their last character.

Strings are stored as arrays of characters, with no inherent size attribute.

The null termination character lets string-processing functions know where the string ends.

Adjacent string constants are concatenated (combined) into one string, with the null termination character added to the end of the final concatenated string.

A string constant can span multiple lines with one of the following methods :

.. code-block:: c

    "Hello, \
    world!"

.. code-block:: c

   "Hello, "
   "world!"

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

White space is the collective term used for several characters:

- The space character
- The tab character
- The newline character
- The vertical tab character
- The form-feed character

White space is ignored (outside of string and character constants), and is therefore optional, except when it is used to separate tokens.

Although you must use white space to separate many tokens, no white space is required between operators and operands, nor is it required between other separators and that which they separate.

Furthermore, wherever one space is allowed, any amount of white space is allowed.

In string constants, spaces and tabs are not ignored; rather, they are part of the string.


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
