##########################
The C programming language
##########################

This is a personal C documentation with essential informations.

It is meant to be used by someone who is already familiar with the language.

It is based on `The GNU C Reference Manual <https://www.gnu.org/software/gnu-c-manual/gnu-c-manual.html>`_.

This documentation consists of two C standards :

- The C99 standard
- The GNU extensions to standard C


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

When using GNU extensions, you can also include the dollar sign character ‘$’ in identifiers.


Keywords
========

Keywords are special identifiers reserved for use as part of the programming language itself.

You cannot use them for any other purpose.


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

Primitive Types
===============

Integer Types
-------------

The integer data types range in size from at least 8 bits to at least 64 bits.

You should use integer types for storing whole number values (and the char data type for storing characters).

The sizes and ranges listed for these types are minimums; depending on your computer platform, these sizes and ranges may be larger.

+----------------------------+----------------------+------------------------------------------------------------+
| Data Type                  | Size                 | Value Range                                                |
+============================+======================+============================================================+
| ``signed char``            | 8 bits               | -128 to 127                                                |
+----------------------------+----------------------+------------------------------------------------------------+
| ``unsigned char``          | 8 bits               | 0 to 255                                                   |
+----------------------------+----------------------+------------------------------------------------------------+
| ``char``                   | 8 bits               | -128 to 127 (or 0 to 255)                                  |
+----------------------------+----------------------+------------------------------------------------------------+
| ``short int``              | 16 bits              | -32,768 to 32,767                                          |
+----------------------------+----------------------+------------------------------------------------------------+
| ``unsigned short int``     | 16 bits              | 0 to 65,535                                                |
+----------------------------+----------------------+------------------------------------------------------------+
| ``int``                    | 32 bits              | -2,147,483,648 to 2,147,483,647                            |
+----------------------------+----------------------+------------------------------------------------------------+
| ``unsigned int``           | 32 bits              | 0 to 4,294,967,295                                         |
+----------------------------+----------------------+------------------------------------------------------------+
| ``long int``               | 32 bits (or 64 bits) | -2,147,483,648 to 2,147,483,647 (or same as long long int) |
+----------------------------+----------------------+------------------------------------------------------------+
| ``unsigned long int``      | 32 bits (or 64 bits) | 0 to 4,294,967,295 (or same as unsigned long long int)     |
+----------------------------+----------------------+------------------------------------------------------------+
| ``long long int``          | 64 bits              | -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807    |
+----------------------------+----------------------+------------------------------------------------------------+
| ``unsigned long long int`` | 64 bits              | 0 to 18,446,744,073,709,551,615                            |
+----------------------------+----------------------+------------------------------------------------------------+

Real Number Types
-----------------
There are three data types that represent fractional numbers.

While the sizes and ranges of these types are consistent across most computer systems in use today, historically the sizes of these types varied from system to system.

As such, the minimum and maximum values are stored in macro definitions in the library header file float.h.

In this section, we include the names of the macro definitions in place of their possible values; check your system’s float.h for specific numbers.

+-----------------+--------------------+------------------------------+
| Data Type       | Size               | Value Range                  |
+=================+====================+==============================+
| ``float``       | 32 bits            | ``FLT_MIN`` to ``FLT_MAX``   |
+-----------------+--------------------+------------------------------+
| ``double``      | 64 bits            | ``DLB_MIN`` to ``DBL_MAX``   |
+-----------------+--------------------+------------------------------+
| ``long double`` | 80, 92 or 128 bits | ``LDBL_MIN`` to ``LDBL_MAX`` |
+-----------------+--------------------+------------------------------+

All floating point data types are signed.

The real number types provided in C are of finite precision, and accordingly, not all real numbers can be represented exactly.

For this reason, we recommend that you consider not comparing real numbers for exact equality with the == operator, but rather check that real numbers are within an acceptable tolerance.


Complex Number Types
--------------------

GCC introduced some complex number types as an extension.

Similar features were introduced in C, but there were a number of differences.

We describe the standard complex number types first.


Standard Complex Number Types
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

There are three complex types.

- ``float _Complex``
- ``double _Complex``
- ``long double _Complex``

The names here begin with an underscore and an uppercase letter in order to avoid conflicts with existing programs’ identifiers.

However, the ``<complex.h>`` header file introduces some macros which make using complex types easier.

``complex``
    Expands to ``_Complex``

``I``
    A constant of type ``const float _Complex`` having the value of the imaginary unit.

It also declares a number of functions for performing computations on complex numbers.

``creal()``
    Returns the real part of a ``double complex`` number.

``cimag()``
    Returns the imaginary part of a ``double complex`` number.

And many other.


GNU Extensions for Complex Number Types
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The GNU extensions also contains complex types.
There are three floating-point complex types.

- ``__complex__ float``
- ``__complex__ double``
- ``__complex__ long double``

It also allow for complex types other than floating-point, so that you can declare complex character types and complex integer types; in fact ``__complex__`` can be used with any of the primitive data types.

To extract the real part of a complex-valued expression, use the keyword ``__real__``, followed by the expression.
Likewise, use ``__imag__`` to extract the imaginary part.


Enumerations
============

Defining Enumerations
---------------------

Declaring Enumerations
----------------------


Unions
======

Defining Unions
---------------

Declaring Union Variables
-------------------------

Declaring Union Variables at Definition
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Declaring Union Variables After Definition
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Initializing Union Members
^^^^^^^^^^^^^^^^^^^^^^^^^^


Accessing Union Members
-----------------------

Size of Unions
--------------


Structures
==========

Defining Structures
-------------------

Declaring Structure Variables
-----------------------------

Declaring Structure Variables at Definition
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Declaring Structure Variables After Definition
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Initializing Structure Members
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Accessing Structure Members
---------------------------

Bit Fields
----------

Size of Structures
------------------


Arrays
======

Declaring Arrays
----------------

Initializing Arrays
-------------------

Accessing Array Elements
------------------------

Multidimensional Arrays
-----------------------

Arrays as Strings
-----------------

Arrays of Unions
----------------

Arrays of Structures
--------------------


Pointers
========

Declaring Pointers
------------------

Initializing Pointers
---------------------

Pointers to Unions
------------------

Pointers to Structures
----------------------


Incomplete Types
================

Type Qualifiers
===============

Storage Class Specifiers
========================

Renaming Types
==============


*************************
Expressions and Operators
*************************

Expressions
===========

Assignment Operators
====================

Incrementing and Decrementing
=============================

Arithmetic Operators
====================

Complex Conjugation
===================

Comparison Operators
====================

Logical Operators
=================

Bit Shifting
============

Bitwise Logical Operators
=========================

Pointer Operators
=================

The sizeof Operator
===================

Type Casts
==========

Array Subscripts
================

Function Calls as Expressions
=============================

The Comma Operator
==================

Member Access Expressions
=========================

Conditional Expressions
=======================

Statements and Declarations in Expressions
==========================================

Operator Precedence
===================

Order of Evaluation
===================

Side Effects
------------

Sequence Points
---------------

Sequence Points Constrain Expressions
-------------------------------------

Sequence Points and Signal Delivery
-----------------------------------


**********
Statements
**********

Labels
======

Expression Statements
=====================

The if Statement
================

The switch Statement
====================

The while Statement
===================

The do Statement
================

The for Statement
=================

Blocks
======

The Null Statement
==================

The goto Statement
==================

The break Statement
===================

The continue Statement
======================

The return Statement
====================

The typedef Statement
=====================


*********
Functions
*********

Function Declarations
=====================

Function Definitions
====================

Calling Functions
=================

Function Parameters
===================

Variable Length Parameter Lists
===============================

Calling Functions Through Function Pointers
===========================================

The main Function
=================

Recursive Functions
===================

Static Functions
================

Nested Functions
================


***************************
Program Structure and Scope
***************************

Program Structure
=================

Scope
=====

