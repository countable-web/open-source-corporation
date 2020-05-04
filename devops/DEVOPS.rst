DevOps
======

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   Purpose
   Scope
   
Purpose
-------

The purpose of DevOps is that software should always be deployed and
tested reliably and automatically in a way that helps us and our
customers.

DevOps is the practice of writing code and configurations to accomplish
this.

Scope
-----

This page introduces the areas we call DevOps at countable.

Specific Goals of DevOps
------------------------

1. Every code project should be deployed automatically, reliably and
   predictably (by the devs and clients) to production.
2. Every code project should automatically be tested whenever the code
   is changes, and the results should be sent to the team (on Slack).
3. We want to minimize the effort in setting up a new environment (dev,
   prod, CI, stage). These should be as automatic as possible.
4. Every code project should be "staged" automatically whenever the code
   changes (in the ``develop`` branch) so anyone can see the bleeding
   edge version in order to discuss, test, and understand ongoing work.
5. Setting up a new server or developer laptop should be quick and
   painless.
6. We should have a collecting of shared scripts that automate any
   tedious task developers need to accomplish.

CI/CD (Jenkins)
---------------

For every project, we should typically have 3 jenkins jobs, a
``<projectname>-stage``, ``<projectname>-prod``, and
``<projectname>-test``. These use docker-compose configs from the
project repo, ``dc.stage.yml``, ``dc.prod.yml`` and ``dc.test.yml``
respectively. Here is a `video on Countable standard project
structure <https://www.youtube.com/watch?v=8ms2YQtURXM>`__ that explains
these compose templates.

Ideally, each Jenkins job simply clones the appropriate branch onto a
node and runs ``cp dc.<env>.yml && docker-compose up``, but in practice
there may be a few extra steps. One day we may be able to have every
environment just use these two commands in order to deploy.

1. The "stage" environment automatically deploys the ``develop`` branch.
2. The "prod" environment automatically deploys the ``master`` branch.
3. The "test" environment automatically runs the tests on any change in
   the ``develop`` branch and posts the results in Slack.
4. dc.dev.yml is intended for use by developers directly, not Jenkins,
   to manually bootstrap environments.

Tips for debugging CI/CD jobs.

-  First, look at the ``console`` section of your jenkins job to
   indentify the failure.
-  Try reproducing it locally
   ``cp dc.prod.yml docker-compose.override.yml``, and
   ``docker-compose up`` (including any other steps the jenkins job
   does).

Provisioning (Terraform, Ansible)
---------------------------------

We are currently using these tools in some projects to set up nodes to
run our software on.
