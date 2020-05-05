Python
======

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   Purpose
   Scope
   Python Code Standards
      Imports
      Line Length
   Debugging Python
      There is a trace in Library code and you want to look around
      The program is really unstable and you want to debug whenever it crashes.

Purpose
-------

Capture our coding standards for Python projects, alongside other things that are useful to know when working on Python codebases at Countable.

Scope
-----

Aggregation of all Python-specific standards, best practices, and known problems we may encounter.

Python Code Standards
---------------------

For Python code, please comply with PEP-8. Editor plugins can automate
most of the rules for you. Common mistakes:

-  Use the ``black`` autoformatter.
-  `Functions should be snake_case <https://www.python.org/dev/peps/pep-0008/#function-names>`__
-  `Classes should be UpperCamelCase <https://www.python.org/dev/peps/pep-0008/#class-names>`__
-  `Constants should be ALL_CAPS <https://www.python.org/dev/peps/pep-0008/#id48>`__

Imports
~~~~~~~

Order imports as follows

::

   # Builtins
   import os
   import sys
   import csv

   # 3rd Party
   import django

   # local
   import mymodule

Line Length
~~~~~~~~~~~

Lines of up to 119 chars are ok, instead of the default 79 chars. The reason for this is we have higher resolution screens these days and 79 chars is crazy restrictive.

Names
-----

-  attributes_names - Attributes (and local variables) should use lowercase with underscores

Debugging Python
----------------

Basics:

-  You should become familiar with Python's debugger, ``pdb`` . Here are a few common cases with recipes.
-  If you want to inspect any object (variable) in python, use the ``dir(obj)`` function in the python CLI (>>>)
-  If you want to know the source file of any module, do ``import module`` and then ``module.__file__``

There is a trace in Library code and you want to look around
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Look at the stack trace, and identify the file and line you want to break at.
2. Add ``import pdb; pdb.set_trace()`` on that line and save the file.
3. Run your program, and when that line is reached the debugger will start interactively in your terminal.


The program is really unstable and you want to debug whenever it crashes.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. Replace the executable ``python`` with ``pdb`` temporarily, in your Dockerfile or docker-compose.yml
2. For example, ``python manage.py runserver`` becomes ``pdb manage.py runserver``
3. Now, restart your web (django) container in the foreground. ie) ``docker-compose stop web && docker-compose up web``
4. When the program crashes, your terminal will halt in a PDB interface and you can print variable names, etc.
