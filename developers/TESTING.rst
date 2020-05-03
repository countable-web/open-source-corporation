Testing
=======

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   Purpose
   Scope
   Testing Principles

Purpose
-------

To establish how and why we do testing at Countable.

Scope
-----

Currently just covers basic testing principles.

Testing Principles
------------------

The goals are to write as few tests as possible for maximum coverage of real world usage (not code coverage).

-  Write tests to increase confidence that our customers' experience will be good.
-  To exercise important flows like signing up, purchasing, core product experience.
-  Prefer e2e tests, the highest possible level, over unit tests (most of the time).
-  Tie test cases to unchanging real world business logic and inputs, not implementation. This prevents their need to be rewritten during refactors.
-  Keep your test scenarios and code as similar as possible to real usage. Your tests should run the backend server, load actual client pages (like selenium would), and flip a switch to trigger test mode in your front end template.
