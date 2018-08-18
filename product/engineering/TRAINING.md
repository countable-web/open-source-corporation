# Developer Training

Tutorials are great to follow through to get the basic operations of any new technology. Find a tutorial that does something you'd like to learn how to do, and with steps that actually work and you can follow yourself, not just read. After that, the best way to learn something is by doing it. Use it for a project, and put in the time tinkering with it. Once you tinker for a while playing with the basics of what you know, you'll start to feel more confident and familiar, have questions about things that you can't resolve through playing around, and want to move on. At this point, find a good tutorial on the next material you want to study.

For this training, be sure to follow the practices [here](../engineering).

# Core Training

All developers should do these parts.

## Kick Off

Clone [this repository] (our operations manual).

```
git clone https://github.com/countable-web/open-source-corporation.git
```

We recommend installing an editor, like Sublime Text, VS Code, or GitHub Atom (my current favourite). PyCharm can also work well if you prefer an IDE. We'll reimburse a licence if you want one Sublime to PyCharm.

Find a mistake, or something that could be more clear or useful in this repository. Edit the corresponding markdown file you've cloned.

Make a pull request to this repository.

## Docker Training

If you're new to Docker, do this. We use Docker for everything so you should get familiar with the basic concepts of running containers from images, and docker-compose which runs multiple containers at once.

Watch this: https://hackr.io/tutorial/learn-docker-in-12-minutes

Do this tutorial: https://docs.docker.com/compose/django/

To set up a new django environment in Docker.

To go further, consider this course: https://diveintodocker.com/

## Django Training

If you’re new to Django, do this. Most of our back end projects are Django and it's good to know how to structure a back end MVC anyway for any project.

https://docs.djangoproject.com/en/1.11/intro/tutorial01/

# Further Training

These are optional based on what specific gaps you need to fill. I'm starting with a list of resources I've found helpful myself, or have found and can imagine being helpful for our work. To provide a feedback loop on training efficacy, copy [this Trello Ticket](https://trello.com/c/rUsXiFoO/3-training-session-tracker-replace-title)for each section you begin below.

## Javacript Training

   * *intermediate* Functional programming intro - http://reactivex.io/learnrx/
   * *intermediate* Read "Javascript, The Good Parts"
   * *advanced* Watch [Hey Underscore, you're Doing it Wrong](https://www.youtube.com/watch?v=m3svKOdZijA)
   
## Linux

From linuxjourney.com - this site's quite a good overall resource of concise, useful and modular lessons. I've listed the chapters and sections (in parens) that are most useful for our work at Countable here. _The key is to do these exercises while following along and trying out the commands in your own linux terminal._ If you just read, you won't retain very well. These exercise assume you're using `bash`, but some computers may use `zsh` by defualt. To remedy this, just open your shell and type `bash` to be sure the shell matches that in the exercises.
  * Command Line Interface (CLI) - https://linuxjourney.com/lesson/the-shell (all)
  * Permissions - https://linuxjourney.com/lesson/file-permissions (1,2,3,4)
  * Text - https://linuxjourney.com/lesson/stdout-standard-out-redirect# (1,2,3,4,5,9,16)
  * Users - https://linuxjourney.com/lesson/users-and-groups (1,2)
  * Processes - https://linuxjourney.com/lesson/monitor-processes-ps-command (1,7)
  * Filesystem - https://linuxjourney.com/lesson/filesystem-hierarchy (1, 9)
  * Networking - https://linuxjourney.com/lesson/network-basics (1, 2, 3, 4) - this one's not great, no explanation of ports.
  * Domain Name System (DNS) - https://linuxjourney.com/lesson/what-is-dns (all) - not great, a bit wordy.

TODO: If someone is feeling energetic, please create an interactive tutorial bash script with key points from the above linuxjourney.com chapters.

From learnshell.org - Good concept but a bit slow and poor choice of material mostly. This page is ok.
  * Variables - https://www.learnshell.org/en/Variables 

If you want to learn Linux deeply after doing the above, it's hard to beat compiling your own kernel and assembling your own userland.
  * LFS The Book http://www.linuxfromscratch.org/lfs/view/stable/
