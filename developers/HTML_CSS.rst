HTML and CSS Standards at Countable
==================================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   Purpose
   Scope
   HTML Coding Standards
   CSS Coding Standards
   SCSS
   Javascript, HTML and CSS Formatting

Purpose
-------

Documenting Countable's coding standards specific to front-end languages and their formatting.

Scope
-----

Currently covers HTML, CSS, our preferred use of SCSS, and formatting.

HTML Coding Standards
--------------

Opening and closing tag should have same indentation level, or on the same line. Use 4 spaces per indent level. 

Bad:

::

   <div>
       <span>
         </span>
     </div>

Good:

::

   <div>
       <span></span>
   </div>

Inline styles should be avoided (use CSS class). 

Bad:

::

   <div style="background:white"></div>

Good:

::

   <div class="white-bg"></div>

Avoid more than one blank line in a row, but content on a new line is fine.

Bad:

::

   <div>Hi</div>

   <p>and welcome</p>

Good:

::

   <div>
     Hi
   </div>

   <p>and welcome</p>

CSS Coding Standards
--------------------

Use the `Prettier autoformatter and standard <https://github.com/prettier/prettier>`__.

-  Don't use !important
-  Use ``.class`` not ``#id`` for styling, because it is more reusable.
-  Separate globally applicable CSS by typography, colors, layout and reset.
-  Break CSS up by component. Some frameworks encourage or endorce this, but it's a good practice for all projects.
-  Don't use capital letters or underscores for selector (class, id) names. Use dashes and lowerase.
-  Avoid inline styling, use classes instead.

::

   .parent {
       font-weight: bold;
   }
   .parent .child {
       color: #FFFFFF;
   }  

   .next {
       color: #0000FF;
   }

If you want to dive deeper, see `CSS Guidelines <https://cssguidelin.es/>`__

SCSS
----

We prefer to use SCSS over bare CSS. This enabled the following:

-  Use mixins to avoid repeating code, but take care to avoid the output CSS getting too large.
-  Define variables globally with brand colors.
-  Make modular files for each concern, and have SCSS combine them.

Javascript, HTML and CSS Formatting
-----------------------------------

Use the `Prettier autoformatter and standard <https://github.com/prettier/prettier>`__.

For projects using node, and supported editors (like VS Code) you can have a ``.prettierrc.js`` in your project root, like this.

::

   {
         semi: false,
         singleQuote: true,
         tabWidth: 2
   }

Alternatively, in VS Code, you can do ``ctrl-,`` to open settings, and search for "prettier". Scroll down to change the above settings manually.
