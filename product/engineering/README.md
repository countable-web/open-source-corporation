
# Engineering Reference

## Purpose

The purpose of this section is to standardize key (not all) engineering processes in order to improve the team's performance, and take advantage of an experience curve by eliminating arbitrary process differences.

## Scope

This folder is for topics related to programming, technical architecture and DevOps.

## Principles

This is how we build things.

  * [Build a prototype](./PROTOTYPING.md) first to validate everything (market, feasibility, usefulness). It's encouraged to take shortcuts as long as your project is just a prototype and not used in production.
  * When a prototype is validated, it transitions to a product and must be made maintainable. This means changing emphasis to testing the user experience as early as possible, to reducing technical debt for the long term.
  * When working on existing projects (products), always leave things in a little better state than you found it.
  * A developer should be able to read the project's README.md in order to spin up a working environment, and run the tests.
  * We automatically run tests, stage the `develop` branch for anyone to look at, and automatically deploy the project to production from the `master` branch.
  * Be thoughtful of your fellow developers. The goal is your code should be obvious and easy to understand for a new programmer. Stick to conventions, and use comments when your code can't be made obvious. Use TODOs.
  * Take special care with error condition handling as this a key to stability in the long run. For every error case, is it something we need to know about? If so, log it to sentry. If the application is in an invalid state it's better to crash and restart as early as possible (return 500 HTTP code). For validation problems (user error), return a 400 http code and refuse the operation. We don't generally need to tell the team when this happens.

## Stack Chocies

[see here](./STACK_CHOICES.md)

## Operations Manuals For Engineering

  * [Coding Standards](./CODING_STANDARDS.md)
  * [Ops](./OPERATIONS.md)
