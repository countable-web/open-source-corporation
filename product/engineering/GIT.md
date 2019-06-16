# How Countable Uses GIT

This document provides examples of common git workflows to show new developers how we use the [git flow](https://jeffkreeftmeijer.com/git-flow/) branch conventions. However, our feature branches are owned by a single person and very short-lived, see [trunk based development](https://trunkbaseddevelopment.com/). From the latter:

> You should do Trunk-Based Development instead of GitFlow and other branching models that feature multiple long-running branches
> You can either do a direct to trunk commit/push (v small teams) or a Pull-Request workflow as long as those feature branches are short-lived and the product of a single person.


## Contributing To A Project

We use branches to maximize code stability, and they should be merged back in and destroyed as quickly as possible.

I don't like the word "feature", because it implies you're working on your own, possibly for quite a while, before integrating back with your team. This is a recipe for many problems. When you want to contribute to a project, the goals is to have your branch as short-lived as possible without breaking the `develop` branch your team is using. The only reason you're working on a separate .

```
git checkout develop
git checkout -b fireball-spell
```

Do your work, commit, update, push.

```
git commit -a -m "Added the Fireball ability to wizards, Trello ticket #51"
git pull origin develop
git push origin fireball-spell
```

Submit a ull request from `fireball-spell` targetting `develop`. Another developer on the project should [review](#code-reviews) and comment on your changes. When everyone agrees, anyone can merge the changes. The `fireball-spell` branch is then deleted after being merged. Delete the fireball-spell branch (BitBucket has an option to do that automatically when you PR)

## Small non-critical patch (update README.md)

A small documentation changes and tests don't always need a feature branch. It's up to your judgement to decide if it's worth someone else reviewing small changes. If not, commit right to develop.

```
git checkout develop
```

make changes to README.md

```
git commit -a -m "Document deployment steps for trolls."
git pull origin develop
git push origin develop
```

## Hotfix

If production is broken, you want to fastrack a fix into master. Only for emergencies.


```
git checkout master
```

make your bugfix (and no other changes here.)

```
git commit -a -m "Hotfix broken CSS on elven smartphone resolutions."
git pull origin master
git push origin master
```

Then deploy the changes (automated by Jenkins in most projects).

## General Guidelines

  * Commit often, with each logical change in its own commit. If for no other reason, developers who commit multiple times per day are nearly 10% more likely to be satisfied with their jobs (Stack Overflow dev survey, 2017). That's crazy correlation for such a simple behaviour!
  * Use the "imperative voice" for commit messages: *Verb* *noun*. ie) "Remove magic glpyphs from wizard profile card."
  * Don't commit example code. Remove or gitignore it.
  * Don't comment commented code, unless you have another English comment above it explaining why it's commented out, and not deleted.
  * Prefer small, short lived branches.
  * When merging, check you've not missed any merge markers still in unmerged files. `grep -r ">>>>>" .` will normally do this for you for example.
  * We prefer the "monorepo" pattern, which means it's better to have one large repo for a project.
  * Unfinished things (links that go nowhere, or Lorem Ipsum) we don't want to show up live should be moved into their own branch, or commented out. Leave an additional comment indicating why they're commented if you do the latter. These things are fine to commit. Just don't do a Pull Request.
  * Create your pull request and read it on BitBucket yourself before adding reviewers. I catch a ton of my own embarrassing mistakes this way when working with clients' devs.
  * Be careful when merging in the upstream (develop) branch that you don't overwrite anyone else's changes with yours. It pays to look closely at each merge marker.
  
## Code Reviews

  * The reviewer doesn't have to spend a ton of time.
  * The reviewer should understand what the code is doing. If it's unclear, ask in a review comment what it does.
  * Reviewer should point out anything that's not following project conventions. Are we doing something a new way, when a perfectly good way existed before, that we should be following?
  * Try to find and remove any repeated code. then comment on that as well.
  * If you're not in a rush, wait for your buddies to review before merging. Of course, if you're confidnet, and in a hurry to deploy something, you can merge the PR immediately yourself and respond to comments later. Use your judgement. It's better to get a review when possible.

