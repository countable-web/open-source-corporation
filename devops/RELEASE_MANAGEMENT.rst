Release Management
==================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   Purpose
   Scope
   Ideal Release Management Process
   Specific Processes to Employ

Purpose
-------

Lay out our approach to release management.

Scope
-----

This document touches upon first our ideal release management process, then some concrete processes to follow to pursue that ideal.


Ideal Release Management Process
--------------------------------

Each project may have some differences by the ideal release management process should aspire to these goals:

-  Allow developers to efficiently commit code knowing it will be tested
   all at once before release.
-  Implement automated end-to-end (puppeteer) testing of core user flows
   is first, then other tests as desired.
-  Be able to confidently release every sprint (every week usually).

Specific Processes to Employ
----------------------------

Specific processes that help with the above:

-  Developers work on ``feature-branch`` named branches (see
   `GIT <../developers/GIT.rst>`__) and commit and push often. Atomic
   commits increase developer happiness by 10% according to the 2017
   StackOverflow survey.
-  Developers take responsibility for cleaning up their code, testing,
   and then making a Pull Reqeust.
-  The pull request should be reviewed by a peer to adhere to our `code standards <../developers/PROJECT_STANDARDS.rst>`__, ensure the code is readable and self-documenting, and to help us learn from each other.
-  When approved, anyone may merge the Pull Request into ``develop`` (never ``master`` directly)
-  The ``develop`` branch is automatically staged so we can review the product together and report any bugs prior to it being released.
-  Ideally once per week, ``develop`` is auto-merged into ``master`` which triggers a release.
-  Critical bugfixes may bypass the above process by pushing `hotfixes <../developers/GIT.rst>`__ to ``master``. Do this sparingly.
