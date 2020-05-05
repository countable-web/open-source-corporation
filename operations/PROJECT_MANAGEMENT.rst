Project Management
==================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   Purpose
   Scope
   Process
   Tools
      GIT
      Trello
      Screencastify chrome extension
   Things We Want to Improve


Purpose
-------

Set conventions for communication between project stakeholders to maximize our velocity towards objectives.

Scope
-----

This document summarizes project management tooling and practices at Countable to assist with onboarding.

Process
-------

-  Every project has a "Purpose" which must be documented and visible.
-  Every project has at least one `Objective and Key Result <OKRS.rst>`__ every month.
-  We use Scrum like `this <SCRUM.rst>`__.
-  Every day, try to get some `feedback <../peopleops/FEEDBACK_LOOPS.rst>`__ on your work.
-  Every day, coordinate with team mates on slack and prioritize.
-  Work together to minimize the amount of time anyone is blocked or waiting for someone's output as their input. The list of items in which people depend on each other's work is called the `critical path <CRITICAL_PATH.rst>`__.

Tools
-----

GIT
~~~

For developers - We follow the `git flow <https://datasift.github.io/gitflow/IntroducingGitFlow.html>`__ branching conventions loosely. All projects should have a master (production) branch which releases are made from, and a develop (stable)
branch for developers as a foundation to build features on. Feature branches are created from develop and merged back in via pull request when ready. Here are some `examples <../developers/GIT.rst>`__ of how we'd use GIT in different cases.

Trello
~~~~~~

We use Trello for project management, as it allows unlimited access to boards by partners and clients, encouraging collaboration and transparency. See `TRELLO <TRELLO.rst>`__.

Screencastify chrome extension
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Especially when dealing with a remote team, customers tend to be more anxious about project progress and features implementation. To overcome this situation and to keep our customers aware of our current development status we can use this chrome extension to **record short screencasts with a brief summary of the latest changes**. After this,
generate a shareable link and send to them through e-mail, in a **weekly basis**.

-  Don't spend more than 10 minutes to do it, since its just a short and simple video.
-  Be professional in your tone and language.
-  This methodology is particularly useful for front-end changes, since they're visible.
-  In case you're dealing with back-end related work, you can still do the screencast, but your approach should be different: You'll have to explain and summarize what you're working on, and show some important parts of the code that you developed.

Things We Want To Improve
-------------------------

-  Increase transparency of our work to clients, team mates, managers.
-  Dashboard for client.
-  Performance metrics, data for retrospectives.
-  Automate timesheets, and invoices using Trello card data.
-  Automate moving trello cards based on commits.
-  Simple to explain to new people. Mostly automated. Avoid slowing down developers who are less oriented to PM process.
-  Link bitbuckets commits.
-  Easy for clients to submit a ticket. Bug or Feature, URL, screenshot.
-  Provide our customers with a constant feedback loop, updating them upon a new feature release or any significant changes on their current project.
