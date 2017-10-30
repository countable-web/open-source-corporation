# Git Flow Usage Examples

## Working on a feature

If there isn't one already, create a new branch for the feature, based on `develop`.

```
git checkout develop
git checkout -b fireball-spell
```

Do you work work, commit, push.

```
git commit -a -m "Added the Fireball ability to wizards, Trello ticket #51"
git push origin fireball-spell
```

Do a pull request from `fireball-spell` targetting `develop`.

## Documentation change (update README.md)

A small documentation change doesn't need a feature branch, just commit to develop.

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

Then deploy the changes (different for every project currently).

