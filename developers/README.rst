Engineering Reference
=====================

Purpose
-------

The purpose of this section is to standardize key (not all) engineering
processes in order to improve the team's performance, and take advantage
of an experience curve by eliminating arbitrary process differences.

Scope
-----

This folder is for topics related to programming, technical architecture
and DevOps.

Principles
----------

This is how we build things.

-  `Build a prototype <./PROTOTYPING.md>`__ first to validate everything
   (market, feasibility, usefulness). It's encouraged to take shortcuts
   as long as your project is just a prototype and not used in
   production.
-  Get feedback on your work by shipping it to real users at least once
   a week, ideally every day. If you can't ship to real users, ship as
   much as you can to internal stakeholders.
-  When a prototype is validated, it transitions to a product and must
   be made maintainable. This means changing emphasis to testing the
   user experience as early as possible, to reducing technical debt for
   the long term.
-  When working on existing projects (products), always leave things in
   a little better state than you found it.
-  Take special care with error condition handling as this a key to
   stability in the long run. For every error case, is it something we
   need to know about? If so, log it to sentry. If the application is in
   an invalid state it's better to crash and restart as early as
   possible (return 500 HTTP code). For validation problems (user
   error), return a 400 http code and refuse the operation. We don't
   generally need to tell the team when this happens.
-  We have `Coding Standards <./CODING_STANDARDS.md>`__ based on
   autoformatters where possible.
-  We operate based on principles in 12factor.net, see `implementation
   here <./OPERATIONS.md>`__
-  We structure projects in a `standard
   way <./CODE_PROJECT_STANDARDS.md>`__ accoring to what we've learned.
-  We are intentional about what dependencies we include in `our
   stack <./STACK_CHOICES.md>`__
