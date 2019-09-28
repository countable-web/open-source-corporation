# How Countable Uses GIT

Countable uses [git flow](https://jeffkreeftmeijer.com/git-flow/) for branch naming. But, the big problem with Git Flow is it seems to encourage huge feature branches, which are a bad idea. Our feature branches are owned by a single person and very short-lived, see [trunk based development](https://trunkbaseddevelopment.com/). From the latter:

> You should do Trunk-Based Development instead of GitFlow and other branching models that feature multiple long-running branches. 
> You can either do a direct to trunk commit/push (v small teams) or a Pull-Request workflow as long as those feature branches are short-lived and the product of a single person.


## Contributing To A Project

Check out `develop` and make a branch from that.

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

Test that your changes dont't break anything. Run automated tests and check things you know other team members are actively working on still work.

Submit a pull request from `fireball-spell` targetting `develop`. Another developer on the project should [review](#code-reviews) and comment on your changes. When everyone agrees, anyone can merge the changes. The `fireball-spell` branch is then deleted after being merged.

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
  * Don't commit commented code, unless you have another English comment above it explaining why it's commented out, and not deleted.
  * Prefer small, short lived branches. _We can't repeat this enough._
  * When merging, check you've not missed any merge markers still in unmerged files. `grep -r ">>>>>" .` will normally do this for you for example.
  * We use the "monorepo" pattern, which means it's better to have one large repo for an entire project. Not multiple small ones for components.
  * Unfinished things (links that go nowhere, or Lorem Ipsum) we don't want to show up live should be deleted, fixed, or commented out. Leave an additional comment indicating why they're commented if you do the latter. These things are fine to commit, but before you do a Pull Request, please review your own code and clean it up so it's something you're proud to show your team.
  * Create your pull request and read it on BitBucket yourself first. I catch a ton of my own embarrassing mistakes this way before my team sees the.
  * Be careful when merging in the upstream (develop) branch that you don't overwrite anyone else's changes with yours. It pays to look closely at each merge marker. Use a [3-way merge tool](https://www.youtube.com/watch?v=GiXGYQ9Ah0U) `git mergetool` if the merge is nontrivial.
  
## Code Reviews
  * The main goal of code reviews is for everyone to learn from each other. So, ask your questions!
  * We don't rely on reviews to catch bugs (that's a bonus if we find one). We rely on tests and the discipline of the original developer for that.
  * It's up to the reviewer's judgement how much time they spend on a code review. It could be quick or more in-depth.
  * The reviewer should understand what the code is doing. If it's unclear, ask in a review comment what it does.
  * Reviewer should point out anything that's not following project conventions. Are we doing something a new way, when a perfectly good way existed before, that we should be following?
  * Try to find and remove any repeated code. then comment on that as well.
  * Code reviews are _not a gate_ for deployment. Anyone can merge the code at any time based on the team's needs. Communicate about what you're doing. If code is merged before you review, the reviewer can still add comments and changes can be patched in as needed.
  * Review these [Code Review Guidelines](https://phauer.com/2018/code-review-guidelines/)
