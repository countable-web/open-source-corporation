Countable Docker Guide
======================

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   Purpose
   Scope
   Docker Basics
   Setting Up An Environment
   Editing the Dockerfiles
   Troubleshooting

Purpose
-------

Describe the importance of Docker to our dev workflow.

Scope
-----

Covers the basics and getting set up, as well as providing resources for more in-depth learning.

Docker Basics
-------------
We have some training materials on Docker `here <./DOCKER_TRAINING.md>`__

We use Docker to manage dev, test, stage and prod environments. Specific conventions we follow:

-  It should be as easy and quick as possible to set up a new environment.
-  production and development environments should be as similar as possible (or, as practical anyway).
-  Base your Dockerfiles on official dockerhub.com images where they exist.
-  ``docker-compose.yml`` contains the Docker config which is the same between every environment.
-  A file called ``dc.dev.yml`` should exist with any settings that vary between environments. In a dev environment, to set up you would copy it and modify it locally with ``cp dc.dev.yml docker-compose.override.yml``. Similar for ``dc.stage.yml`` and ``dc.prod.yml`` for other environments respectively. Our CI testing environments can use ``dc.dev.yml``. ``docker-compose.override.yml`` should be in ``.gitignore``
-  The docker-compose.override.yml file should only contain differences between dev and prod and other environments. This includes the ports, restart policy, secrets, and normally not much else. If a line doesn't need to be in the overrides for a specific reason, move it to the main docker-compose.yml instead.

Setting Up An Environment
-------------------------

1. `Install Docker on your machine <https://docs.docker.com/engine/installation/>`__

2. Clone one of our beautiful apps. ``git clone <repo>``

3. Copy the docker override template: ``cp dc.dev.yml docker-compose.override.yml``

4. Run docker-compose: ``docker-compose up``

5. Navigate to `http://localhost <http://localhost>`__. Ensure only one project is running at a time if you're using port 80 (as we do here)

Editing the Dockerfiles
-----------------------

When you change something about the operating system environment your container exposes, such as installing a new package, this is often done in the Dockerfile itself. This will result in changes being propagated to other environments including production when you commit the modified Dockerfile, triggering a Docker build there. However, if you modify a file used during the build step such as requirements.txt , other environments won't be updated by default. To force environments to rebuild, commit a small change to the Dockerfile. Our convention is:

::

   RUN echo "bust cache 33 (version)"

Bumping this version will trigger the rebuild as desired.

Troubleshooting
---------------

When starting with Docker there are a few common issues:

-  A port you need is blocked. Typically our apps run on port 80. To see if something's running there, ``sudo lsof -n -i :80 | grep LISTEN`` on Linux, Mac.
-  Make sure you have a docker-compose.override.yml with port 80 mapped to your application.
