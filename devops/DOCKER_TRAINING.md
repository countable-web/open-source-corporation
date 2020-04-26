# Docker Training

## Purpose

This explains the basics of using Docker, specifically written for Countable devs. If you want to know WHY we use docker, see [A Pure Docker Workflow](https://docs.google.com/document/d/1F_LvoR1R6_GEiwqBWviYVXLUuOnzSl-q5WcFspYqmUY/edit#heading=h.dgi1cb6nx4tu) and [The Allure Of Docker](https://docs.google.com/document/d/1aWJFw5DcBC0sj1x2UukruNSldfxMAJqO3fBqzx6ubDQ/edit)

## Scope

Basic docker for new devs. It assumes you did [these exercises on Linux](https://github.com/countable-web/open-source-corporation/blob/master/product/engineering/TRAINING.md#linux).

## Docker 101

Docker is a command line interface (CLI), and also a Linux daemon for running containers from images. Let's define those two terms:

A Docker container is:
  * Like a lightweight virtual machine (VM), so in some ways Docker is comparable to Vagrant or other VM scripting environment.
  * A single [chrooted](https://en.wikipedia.org/wiki/Chroot) process, run when the container is created. It's just like any process in the operating system, but it has its own filesystem.
  * Created from an image.

A Docker image is:
  * Used to create and run containers.
  * The filesystem the container runs in, together with what command it runs. For example, run the command `pwd` in a stock Ubuntu filesystem would be an image, and you could "run" it to create a container that actually executes that command. The actual command to do this is `docker run ubuntu pwd` FYI.
  * Defined by a Dockerfile, a text file that indicates what's in the image and what command it runs. ie) Ubuntu, with Python 3 installed, which opens a Python prompt by default.

Functionally, the most obvious difference with a container is that it starts up very quickly, in seconds instead of minutes.

First, install Docker. It's really easy on Linux, which you should be using. You could also consider using [the official sandbox](https://training.play-with-docker.com/ops-s1-hello/) for this similar lab hosted by Docker the company.

You should add yourself to the docker group.

```
usermod -aG `whoami` docker
```

Now you can access the Docker CLI.

```
docker
```

This just prints out the help, and list of commands available for managing containers. We care mostly about these for now:
  * `docker run` - creates and starts a container.
  * `docker start` - starts an existing container.
  * `docker stop` - stops a container.
  * `docker rm` - removes a stopped container.
  * `docker ps` - shows currently running containers.
  * `docker ps -a` - shows all existing containers.
  * `docker exec` - executes a shell command inside a specified running container.
  * *BONUS* `docker cp` - copies a file into or out of a container.

This is mostly what we as web developers know as a CRUD (Create, Read, Update, Delete) for containers.

Let's do an example:

Create a container from the hello-world image (provided by Docker to greet you).

```
docker run hello-world
```
There, you've run a mini Linux VM. Congrats! It printed some stuff out, and exited. That's because by default, this image just runs a script that says Hello to us.

Let's look at your container. It's already exited so you won't see anything with:
```
docker ps
```

which only shows running containers. You have to do:
```
docker ps -a

CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                          PORTS               NAMES
4876208e98d8        hello-world                            "/hello"                 4 minutes ago       Exited (0) 4 minutes ago                                 flamboyant_sinoussi
```

There we go! A table of info about the container. We can see it's ID, what image was used to create it, the command that was run, its age, status, ports, and optional name (a nicer ID).

Let's switch to another image called `python:alpine`, which has Python in it already. We'll specify `-it` which means we want to interact with the container directly when it's running.

```
docker run -it python:alpine
```

Nice, a python shell! You can run Python or any other scripting language or database this way directly in Docker without installing it on your host. It's isolated and can be easily removed.

Try some other commands in this container. Just append the command you want. Each time you'll create a new container, and it will complete your command and then exit:

```
docker run -it python:alpine ls
```

Look, it's the root of the container's Linux filesystem with all the usual folders like `etc` and `bin`.

```
docker run -it python:alpine pwd
````

We start off in the root (/) directory.

```
docker run -it python:alpine whoami
```

Docker containers run as the `root` (admin) user by default.

```
docker run -it python:alpine ps
```

Just as promised, there's only one process. It's the `ps` process you just run. All the other commands earlier died in their containers when they finished. Now, we've made quite a mess! Let's delete all these containers!

```
docker ps -a
```

To get all the container IDs, and then

```
docker rm <ID>
```

To get rid of the containers you no longer want.

When we're developing web apps, we normally want to run a web server, database or any other service we need.
We normally run these in the "background", meaning we don't want to see their output on our screen directly, so we use `-d` instead of `-it`.

As an example of this, let's create a container that lasts a long time. It can just "sleep" for a day. Let's give it a name, `sleepy` as well:
```
docker run --name sleepy python:alpine sleep
```

Now, we can see the container running with:
```
docker run -d --name sleepy python:alpine sleep 1d
```

There it is, sleeping away.
```
docker ps
```

Let's copy a file into the container!
```
touch file.txt
docker cp file.txt sleepy:/
docker exec -it sleepy ls
```

We can see the root folders as before, but now `file.txt` is also there!

Let's stop it.

```
docker stop sleepy
```

It's only viewable with `docker ps -a` now because it's stopped.
```
docker ps
docker ps -a
```

Let's delete it.
```
docker rm
docker ps -a
```

Gone. Ok, what about images? They just seem to take care of themselves. Well, you can see them too. Docker's downloaded some you needed earlier.

```
docker images
```

There they are.

