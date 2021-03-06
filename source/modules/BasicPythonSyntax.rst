Basic Python Syntax
===================

(Follow along in the iPython interpreter...)

.. rst-class:: center mlarge


| Values, Types, and Symbols
|
| Expressions and Statements


Values
------

All of programming is really about manipulating values.

.. rst-class:: build

* Values are pieces of unnamed data: ``42``, ``'Hello, world'``

* In Python, all values are objects

  - Try ``dir(42)``  - lots going on behind the curtain!

* Every value has a type

  - Try ``type(42)`` - the type of a value determines what it can do

.. ifslides::

    .. rst-class:: centered

        [demo]


Literals for the Basic Value types:
------------------------------------

Numbers:
  - floating point: ``3.4``
  - integers: ``456``

Text:
  -  ``"a bit of text"``
  -  ``'a bit of text'``
  - (either single or double quotes work -- why?)

Boolean values:
  -  ``True``
  -  ``False``

The nothing object:
  - ``None``

(There are intricacies to all of these that we'll get into later)


Code structure
--------------

Each line is a piece of code.

Comments:

.. code-block:: ipython

    In [3]: # everything after a '#' is a comment

Expressions:

.. code-block:: ipython

    In [4]: # evaluating an expression results in a value

    In [5]: 3 + 4
    Out[5]: 7

.. nextslide::

Statements:

.. code-block:: ipython

    In [6]: # statements do not return a value, may contain an expression

    In [7]: line_count = 42

    In [8]: return something


.. nextslide:: The Print Function

It is somewhat obvious, but handy when playing with code:

.. code-block:: ipython

    In [1]: print ("something")
    something

You can print multiple things:

.. code-block:: ipython

    In [2]: print("the value is", 5)
    the value is 5


.. nextslide::

Any python object can be printed (though it might not be pretty...)

.. code-block:: ipython

    In [1]: class bar(object):
       ...:     pass
       ...:

    In [2]: print(bar)
    <class '__main__.bar'>


.. nextslide:: Code Blocks

Blocks of code are delimited by a colon and indentation:

.. code-block:: python

    def a_function():
        a_new_code_block
    end_of_the_block

.. code-block:: python

    for i in range(100):
        print(i**2)

.. code-block:: python

    try:
        do_something_bad()
    except:
        fix_the_problem()

.. nextslide::

Python uses indentation to delineate structure.

This means that in Python, whitespace is **significant**.

(but **ONLY** for newlines and indentation)

The standard is to indent with **4 spaces**.

**SPACES ARE NOT TABS**

**TABS ARE NOT SPACES**


.. nextslide::

These two blocks look the same:

.. code-block:: python

    for i in range(100):
        print(i**2)

.. code-block:: python

    for i in range(100):
        print(i**2)


.. nextslide::

But they are not:

.. code-block:: python

    for i in range(100):
    \s\s\s\sprint i**2

.. code-block:: python

    for i in range(100):
    \tprint i**2

**ALWAYS INDENT WITH 4 SPACES**


.. nextslide::

.. rst-class:: center large

NEVER INDENT WITH TABS

Make sure your editor is set to use spaces only --

Even when you hit the <tab> key

[Python itself allows any number of spaces (and tabs), but you are just going to confuse yourself and others if you do anything else]


Expressions
------------

An *expression* is made up of values and operators.

.. rst-class:: build

* An expression is evaluated to produce a new value:  ``2 + 2``

  *  The Python interpreter can be used as a calculator to evaluate expressions

* Integer vs. float arithmetic

  * (Python 3 smooths this out)
  * Always use ``/`` when you want division with float results, ``//`` when you want floored (integer) results (no remainder).

* Type conversions

  * This is the source of many errors, especially in handling text

* Type errors - checked at run time only

.. ifslides::

    .. rst-class:: centered

        [demo]


Symbols
-------

Symbols are how we give names to values (objects).

.. rst-class:: build

* Symbols must begin with an underscore or letter
* Symbols can contain any number of underscores, letters and numbers

  * this_is_a_symbol
  * this_is_2
  * _AsIsThis
  * 1butThisIsNot
  * nor-is-this

* Symbols don't have a type; values do

  * This is why python is "Dynamic"


Symbols and Type
----------------

Evaluating the type of a *symbol* will return the type of the *value* to which
it is bound.

.. code-block:: ipython

    In [19]: type(42)
    Out[19]: int

    In [20]: type(3.14)
    Out[20]: float

    In [21]: a = 42

    In [22]: b = 3.14

    In [23]: type(a)
    Out[23]: int

    In [25]: a = b

    In [26]: type(a)
    Out[26]: float

*wait!* ``a`` has a different type?!? -- yes, because it's the type of the value: "3.14", names don't actually have a type, the same name can refer to any type.


Assignment
----------

A *symbol* is **bound** to a *value* with the assignment operator: ``=``

.. rst-class:: build

* This attaches a name to a value
* A value can have many names (or none!)
* Assignment is a statement, it returns no value


.. nextslide::

Evaluating the name will return the value to which it is bound

.. code-block:: ipython

    In [26]: name = "value"

    In [27]: name
    Out[27]: 'value'

    In [28]: an_integer = 42

    In [29]: an_integer
    Out[29]: 42

    In [30]: a_float = 3.14

    In [31]: a_float
    Out[31]: 3.14

Variables?
----------

.. rst-class:: build

* In most languages, what Python calls symbols or names are called "variables".

* In fact, we will probably call them variables in this class.

* That's because they are used, for the most part, for the same purposes.

* But often a "variable" is defined as something like:
  "a place in memory that can store values"

* That is **NOT** the same thing as a symbol or name in Python!

* A name can be bound to a value -- but that has nothing to do with a
  location in memory.

In-Place Assignment
-------------------

You can also do "in-place" assignment with ``+=``.

.. code-block:: ipython

    In [32]: a = 1

    In [33]: a
    Out[33]: 1

    In [34]: a = a + 1

    In [35]: a
    Out[35]: 2

    In [36]: a += 1

    In [37]: a
    Out[37]: 3

also: ``-=, *=, /=, **=, \%=``

(not quite -- really in-place assignment for mutables....)


Multiple Assignment
-------------------

You can assign multiple names from multiple expressions in one
statement

.. code-block:: ipython

    In [48]: x = 2

    In [49]: y = 5

    In [50]: i, j = 2 * x, 3 ** y

    In [51]: i
    Out[51]: 4

    In [52]: j
    Out[52]: 243


Python evaluates all the expressions on the right before doing any assignments


Nifty Python Trick
------------------

Using this feature, we can swap values between two names in one statement:

.. code-block:: ipython

    In [51]: i
    Out[51]: 4

    In [52]: j
    Out[52]: 243

    In [53]: i, j = j, i

    In [54]: i
    Out[54]: 243

    In [55]: j
    Out[55]: 4

Multiple assignment and symbol swapping can be very useful in certain contexts

Deleting
--------

You can't actually directly delete values in python...

``del`` only deletes a name (or "unbinds" the name...)

.. code-block:: ipython

    In [56]: a = 5

    In [57]: b = a

    In [58]: del a

    In [59]: a
    ---------------------------------------------------------------------------
    NameError                                 Traceback (most recent call last)
    <ipython-input-59-60b725f10c9c> in <module>()
    ----> 1 a

    NameError: name 'a' is not defined

.. nextslide::

The object is still there...python will only delete it if there are no
references to it.

.. code-block:: ipython

    In [15]: a = 5

    In [16]: b = a

    In [17]: del a

    In [18]: a
    ---------------------------------------------------------------------------
    NameError                                 Traceback (most recent call last)
    <ipython-input-18-60b725f10c9c> in <module>()
    ----> 1 a

    NameError: name 'a' is not defined

    In [19]: b
    Out[19]: 5


Identity
--------

Every value in Python is an object.

Every object is unique and has a unique *identity*, which you can inspect with
the ``id`` *builtin*:

.. code-block:: ipython

    In [68]: id(i)
    Out[68]: 140553647890984

    In [69]: id(j)
    Out[69]: 140553647884864

    In [70]: new_i = i

    In [71]: id(new_i)
    Out[71]: 140553647890984


Testing Identity
----------------

You can find out if the values bound to two different symbols are the **same
object** using the ``is`` operator:

.. code-block:: ipython

    In [72]: count = 23

    In [73]: other_count = count

    In [74]: count is other_count
    Out[74]: True

    In [75]: count = 42

    In [76]: other_count is count
    Out[76]: False

.. ifslides::

    .. rst-class:: centered

        [demo]

**NOTE:** checking the id of an object, or using "is" to check if two objects are the same is rarely used except for debugging and understanding what's going on under the hood. They are not used regularly in production code.


Equality
--------

You can test for the equality of certain values with the ``==`` operator

.. code-block:: ipython

    In [77]: val1 = 20 + 30

    In [78]: val2 = 5 * 10

    In [79]: val1 == val2
    Out[79]: True

    In [80]: val3 = '50'

    In [81]: val1 == val3
    Out[84]: False

A string is never equal to a number!

.. ifslides::

    .. rst-class:: centered

        [demo]

Singletons
----------

Python has three "singletons" -- value fro which there is only one instance:

  ``True``, ``False``, and ``None``

To check if a name is bound to one of these, you use ``is``::

    a is True

    b is False

    x is None

Note that in contrast to english -- "is" is asking a question, not making an assertion -- ``a is True`` means "is a the True value?"

Operator Precedence
-------------------

Operator Precedence determines what evaluates first:

.. code-block:: python

    4 + 3 * 5 != (4 + 3) * 5

To force statements to be evaluated out of order, use parentheses -- expressions in parentheses are always evaluated first:

   (4 + 3) * 5 != 4 + (3 * 5)

Python follows the "usual" rules of algebra.

Python Operator Precedence
--------------------------

Parentheses and Literals:
  ``(), [], {}``

  ``"", b'', ''``

Function Calls:
  ``f(args)``

Slicing and Subscription:
  ``a[x:y]``

  ``b[0], c['key']``

Attribute Reference:
  ``obj.attribute``

.. nextslide::

Exponentiation:
  ``**``

Bitwise NOT, Unary Signing:
  ``~x``

  ``+x, -x``

Multiplication, Division, Modulus:
  ``*, /, %``

Addition, Subtraction:
  ``+, -``

.. nextslide::

Bitwise operations:
  ``<<, >>,``

  ``&, ^, |``

Comparisons:
  ``<, <=, >, >=, !=, ==``

Membership and Identity:
  ``in, not in, is, is not``

Boolean operations:
  ``or, and, not``

Anonymous Functions:
  ``lambda``


String Literals
---------------

A "string" is a chunk of text.

You define a ``string`` value by writing a string *literal*:

.. code-block:: ipython

    In [1]: 'a string'
    Out[1]: 'a string'

    In [2]: "also a string"
    Out[2]: 'also a string'

    In [3]: "a string with an apostrophe: isn't it cool?"
    Out[3]: "a string with an apostrophe: isn't it cool?"

    In [4]: 'a string with an embedded "quote"'
    Out[4]: 'a string with an embedded "quote"'


.. nextslide::

.. code-block:: ipython

    In [5]: """a multi-line
       ...: string
       ...: all in one
       ...: """
    Out[5]: 'a multi-line\nstring\nall in one\n'

    In [6]: "a string with an \n escaped character"
    Out[6]: 'a string with an \n escaped character'

    In [7]: r'a "raw" string, the \n comes through as a \n'
    Out[7]: 'a "raw" string, the \\n comes through as a \\n'

Python3 strings are fully support Unicode, which means that it can suport literally all the languages in the world (and then some -- Klingon, anyone?)

Because Unicode is native, you can get very far without even thinking about it. Anything you can type in your editor will work fine.


Keywords
--------

Python defines a number of **keywords**

These are language constructs.

You *cannot* use these words as symbols.

::

    and       del       from      not       while
    as        elif      global    or        with
    assert    else      if        pass      yield
    break     except    import    print
    class     exec      in        raise
    continue  finally   is        return
    def       for       lambda    try

.. nextslide::


If you try to use any of the keywords as symbols, you will cause a
``SyntaxError``:

.. code-block:: ipython

    In [13]: del = "this will raise an error"
      File "<ipython-input-13-c816927c2fb8>", line 1
        del = "this will raise an error"
            ^
    SyntaxError: invalid syntax

.. code-block:: ipython

    In [14]: def a_function(else='something'):
       ....:     print(else)
       ....:
      File "<ipython-input-14-1dbbea504a9e>", line 1
        def a_function(else='something'):
                          ^
    SyntaxError: invalid syntax


__builtins__
------------

Python also has a number of pre-bound symbols, called **builtins**

Try this:

.. code-block:: ipython

    In [6]: dir(__builtins__)
    Out[6]:
    ['ArithmeticError',
     'AssertionError',
     'AttributeError',
     'BaseException',
     'BufferError',
     ...
     'vars',
     'xrange',
     'zip']

.. nextslide::

You are free to rebind these symbols:

.. code-block:: ipython

    In [15]: type('a new and exciting string')
    Out[15]: str

    In [16]: type = 'a slightly different string'

    In [17]: type('type is no longer what it was')
    ---------------------------------------------------------------------------
    TypeError                                 Traceback (most recent call last)
    <ipython-input-17-907616e55e2a> in <module>()
    ----> 1 type('type is no longer what it was')

    TypeError: 'str' object is not callable

In general, this is a **BAD IDEA** -- hopefully your editor will warn you.


Exceptions
----------

Notice that the first batch of ``__builtins__`` are all *Exceptions*

Exceptions are how Python tells you that something has gone wrong.

There are several exceptions that you are likely to see a lot of:

.. rst-class:: build

* ``NameError``: indicates that you have tried to use a symbol that is not bound to a value.

* ``TypeError``: indicates that you have tried to use the wrong kind of object for an operation.

* ``SyntaxError``: indicates that you have mis-typed something.

* ``AttributeError``: indicates that you have tried to access an attribute or
  method that an object does not have (this often means you have a different
  type of object than you expect)


Functions
---------

What is a function?

.. rst-class:: build

A function is a self-contained chunk of code

You use them when you need the same code to run multiple times,
or in multiple parts of the program.

(DRY) -- "Don't Repeat Yourself"

Or just to keep the code clean

Functions can take and return information

.. nextslide::

The minimal Function has at least one statement

.. code-block:: python

    def a_name():
        a_statement

.. nextslide::

Pass Statement does nothing (Note the indentation!)

.. code-block:: python

    def minimal():
        pass

This, or course, is not useful -- you will generally have multiple statements in a function -- and they will do something.

Functions: ``def``
------------------

``def``  is a *statement*:

  * it is executed
  * it creates a local name
  * it does *not* return a value

.. nextslide::

function defs must be executed before the functions can be called:

.. code-block:: ipython

    In [23]: unbound()
    ---------------------------------------------------------------------------
    NameError                                 Traceback (most recent call last)
    <ipython-input-23-3132459951e4> in <module>()
    ----> 1 unbound()

    NameError: name 'unbound' is not defined

.. code-block:: ipython

    In [18]: def simple():
       ....:     print("I am a simple function")
       ....:

    In [19]: simple()
    I am a simple function


Calling Functions
-----------------

You **call** a function using the function call operator (parens):

.. code-block:: ipython

    In [2]: type(simple)
    Out[2]: function

    In [3]: simple
    Out[3]: <function __main__.simple>

    In [4]: simple()
    I am a simple function

Calling a function is how you run the code in that function.


Functions: Call Stack
---------------------

functions call functions -- this makes an execution stack -- that is what a "trace back" is:

.. code-block:: ipython

    In [5]: def exceptional():
       ...:     print("I am exceptional!")
       ...:     print 1/0
       ...:
    In [6]: def passive():
       ...:     pass
       ...:
    In [7]: def doer():
       ...:     passive()
       ...:     exceptional()
       ...:

You've defined three functions, one of which will *call* the other two.


Functions: Tracebacks
---------------------

.. code-block:: ipython

    In [8]: doer()
    I am exceptional!
    ---------------------------------------------------------------------------
    ZeroDivisionError                         Traceback (most recent call last)
    <ipython-input-8-685a01a77340> in <module>()
    ----> 1 doer()

    <ipython-input-7-aaadfbdd293e> in doer()
          1 def doer():
          2     passive()
    ----> 3     exceptional()
          4

    <ipython-input-5-d8100c70edef> in exceptional()
          1 def exceptional():
          2     print("I am exceptional!")
    ----> 3     print(1/0)
          4

    ZeroDivisionError: integer division or modulo by zero

The error occurred in the ``doer`` function -- but the traceback shows you where that was called from. In a more complex system, this can be VERY useful -- learn to read tracebacks!


Functions: ``return``
---------------------

Every function ends by returning a value

This is actually the simplest possible function:

.. code-block:: python

    def fun():
        return None

.. nextslide::

if you don't explicilty put ``return``  there, Python will:

.. code-block:: ipython

    In [9]: def fun():
       ...:     pass
       ...:
    In [10]: fun()
    In [11]: result = fun()
    In [12]: print(result)
    None

note that the interpreter eats ``None`` -- you need to call ``print()`` to see it.


.. nextslide::

Only one return statement in a function will ever be executed.

Ever.

Anything after a executed return statement will never get run.

This is useful when debugging!

.. code-block:: ipython

    In [14]: def no_error():
       ....:     return 'done'
       ....:     # no more will happen
       ....:     print(1/0)
       ....:
    In [15]: no_error()
    Out[15]: 'done'


.. nextslide::

However, functions *can* return multiple results:

.. code-block:: ipython

    In [16]: def fun():
       ....:     return 1, 2, 3
       ....:
    In [17]: fun()
    Out[17]: (1, 2, 3)


.. nextslide::

Remember multiple assignment?

.. code-block:: ipython

    In [18]: x, y, z = fun()
    In [19]: x
    Out[19]: 1
    In [20]: y
    Out[20]: 2
    In [21]: z
    Out[21]: 3


Functions: parameters
---------------------

In a ``def`` statement, the values written *inside* the parens are
**parameters**

.. code-block:: ipython

    In [22]: def fun(x, y, z):
       ....:     q = x + y + z
       ....:     print(x, y, z, q)
       ....:

x, y, z are *local* names -- so is q


Functions: arguments
--------------------

When you call a function, you pass values to the function parameters as
**arguments**

.. code-block:: ipython

    In [23]: fun(3, 4, 5)
    3 4 5 12

The values you pass in are *bound* to the names inside the function and used.

The name used outside the object is separete from the name used inside teh function:

The ``if`` Statement
---------------------

In order to do anything interesting at all, you need to be able to make a decision.

.. nextslide::

.. code-block:: ipython

    In [12]: def test(a):
       ....:     if a == 5:
       ....:         print("that's the value I'm looking for!")
       ....:     elif a == 7:
       ....:         print("that's an OK number")
       ....:     else:
       ....:         print("that number won't do!")

    In [13]: test(5)
    that's the value I'm looking for!

    In [14]: test(7)
    that's an OK number

    In [15]: test(14)
    that number won't do!

There is more to it than that, but this will get you started.


Enough For Now
--------------

That's it for our basic intro to Python

You now know enough Python to do some basic exercises in Python programming
