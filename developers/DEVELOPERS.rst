Developers Reference
=====================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   Purpose
   Scope
   Principles
   Developer's Guild Meetings
   :ref: 'ARCHITECTURE'
   :ref: 'BUG_REPORTING'
   :ref: 'CODING_STANDARDS'
   :ref: 'DEPENDENCIES'
   :ref: 'DJANGO'
   :ref: 'GIT'
   :ref: 'HTML_CSS'
   :ref: 'INFO_SECURITY_DESIGN'
   :ref: 'JAVASCRIPT'
   :ref: 'PROJECT_STANDARDS'
   :ref: 'PROTOTYPING'
   :ref: 'PYTHON'
   :ref: 'STACK_CHOICES'
   :ref: 'TESTING'
   :ref: 'TRAINING'


Purpose
-------

The purpose of this section is to standardize key (not all) engineering processes in order to improve the team's performance, and take advantage of an experience curve by eliminating arbitrary process differences.

Scope
-----

This folder is for topics related to programming and technical architecture.

Principles
----------

This is how we build things.

- `Build a prototype first <./PROTOTYPING.rst>`__ to validate everything (market, feasibility, usefulness). It's encouraged to take shortcuts as long as your project is just a prototype and not used in production.
-  Get feedback on your work by **shipping it to real users at least once a week, ideally every day**. If you can't ship to real users, ship as much as you can to internal stakeholders.
-  When a prototype is validated, it transitions to a product and must be made maintainable. This means changing emphasis from testing the user experience as early as possible, to reducing technical debt for the long term.
-  When working on existing projects (*products*), always leave things in a little better state than you found it.
-  Take special care with error condition handling, as this a key to stability in the long run. For every error case, is it something we need to know about? If so, log it to Sentry. If the application is in an invalid state it's better to crash and restart as early as possible (return 500 HTTP code). For validation problems (user error), return a 400 http code and refuse the operation. We don't generally need to tell the team when this happens.
-  We have `Coding Standards <./CODING_STANDARDS.rst>`__ based on auto-formatters where possible, which include standards for structuring projects which are based upon what we've learned.
-  We operate based on principles in 12factor.net, see `implementation here <./OPERATIONS.md>`__
-  We are intentional about what dependencies we include in `our stack <./STACK_CHOICES.rst>`__

Developer's Guild Meetings
--------------------------

The developer's guild exists to:

  * Develop lightweight standards, style and conventions that reduce or avoid technical debt and continuously improve code quality across all projects
  * Make it easier for Countable developers to switch projects, knowing what conventions should be used globally.
  * Create a great learning environment where we can all help each other improve as devs.
  * Help Countable deploy better quality work in front of real users more quickly.

We accomplish this via:

  * Monthly meetings with workshops and presentations.
  * Mob / pair coding sessions.
  * Code reviews.