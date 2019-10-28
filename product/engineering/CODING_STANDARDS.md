# Coding Standards and Style

## Purpose

Encourage consistent and effective coding practices in the team.

## Scope

Coding standards and guidelines at Countable Web Productions.
  * This document has arisen out of specific cases where different conventions of developers have caused us to waste time. 
  * We use auto-formatters in place of coding standards in every case possible.

### Principles

  * For projects that do not currently follow our standards (open source, or new projects shared with other dev teams) but follows a different one, stick with that project's conventions unless we make a conscious decision to refactor the whole thing. Don't mix conventions.
  * Make life easier for your team mates and future self by being consistent and thoughtful of what someone unfamiliar would think. The goal is your code should be obvious and easy to understand for a new programmer. Stick to conventions, and use comments to explain the story of your code, and why things are done a particular way.
  * Choose abstractions and tools based on real problems, not the reverse.

### Literature
We are influenced by the following writing.

  * [Domain Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design).
  * 12 factor app
  * Trunk based development
  * Agile manifesto

### Names

  This section refers to the names of variables, database columns, classes, and any other case where a name is chosen in code. [syin] Consider the book "Clean Code" on this topic and on writing short functions.

  * Names should indicate *what* a function does in _business domain language_.
  * Name length should be proportional to the variable's scope size. `x` is ok in a one liner, but not a global.
  * When an industry jargon (domain language) term is available, use that.
  * ClassNames - Classes should use an upper camel case string of nouns
  * attributes_names - Attributes (and local variables) should use lowercase with underscores
  * CONSTANT_NAMES - Constants should be uppercase with underscores.

### Files

  * Filenames should be lowercase with dashes (NOT SPACES) to separate words *except* for Python, which uses underscores in place of dashes.
  * The purpose, and contents of any file should be as obvious as possible by its filename and location.
  * Avoid repeated or unnecessary code, except where doing so is much more clear. Keep in mind less code is actually easier to understand, all other things being equal. So, it bears repeating, use the minimum amount of code in declarative domain language. Using the wrong abstraction can be worse than repeated code.

### Locality

Functional Modules
  * Modules should be responsible for a specific task or set of RELATED tasks.
  * Modules should communicate through easily testable interfaces. A huge heirarchy of objects shouldn't be required to test a single method, because the method should only take arguments it actually uses (not a big tree which happens to contain those)

### Comments

  * Do not comment what is obvious from the code. "# Increment the variable." is not a good comment.
  * Do Document the rationale "why", the reason behind an implementation choice.
  * Use TODO comments to indicate your intent for future work.
  * Comment beside anything that's unintutive or unexpected to another reader.
  * Do not leave actual code commented out unless you have a good reason. If you do have one, document that reason as a comment as well.

### No tabs

We are a Python shop, and so observance of pep 8 leads us to use 4 spaces for indentation. We carry this convention to other languages, using 4 spaces for indentation in CSS, HTML, Javacript, etc. We never use the tab character.

### Docker

Use [Docker](./DOCKER.md) for any web application project (and other projects where applicable). It should be possible to bring up a new environment by only the following for any of our projects.

```
git clone <repo>
cd <project folder>
cp docker-compose.override.yml.dev.template docker-compose.override.yml
docker-compose up
```

TODO: Write a dotfiles script that does all the following with `getproject <project slug>`.

And browsing to http://localhost

Of course, to see anything meaningful you may need to restore a database to your `db` container.


## Python Coding Standards

For Python code, please comply with PEP-8. Editor plugins can automate most of the rules for you. Common mistakes:

  * [Functions should be snake_case](https://www.python.org/dev/peps/pep-0008/#function-names)
  * [Classes should be UpperCamelCase](https://www.python.org/dev/peps/pep-0008/#class-names)
  * [Constants should be ALL_CAPS](https://www.python.org/dev/peps/pep-0008/#id48)

### Imports

Order imports as follows
```
# Builtins
import os
import sys
import csv

# 3rd Party
import django

# local
import mymodule
```

### Line Length

Lines of up to 119 chars are ok, instead of the default 79 chars. The reason for this is we have higher resolution screens these days and 79 chars is crazy restrictive.


## HTML Standards

Opening and closing tag should have same indentation level, or on the same line. Use 4 spaces per indent level.
Bad:
```
<div>
    <span>
      </span>
  </div>
```
Good:
```
<div>
    <span></span>
</div>
```

Inline styles should be avoided (use CSS class).
Bad:
```
<div style="background:white"></div>
```
Good:
```
<div class="white-bg"></div>
```

Avoid more than one blank line in a row, but content on a new line is fine:
Bad:
```
<div>Hi</div>

<p>and welcome</p>
```
Good:
```
<div>
  Hi
</div>

<p>and welcome</p>
```

## CSS Coding Standards

Use the Prettier autoformatter and standard. https://github.com/prettier/prettier

  * Don't use !important
  * Use `.class` not `#id` for styling, because it is more reusable.
  * Separate globally applicable CSS by typography, colors, layout and reset.
  * Break CSS up by component. Some frameworks encourage or endorce this, but it's a good practice for all projects.
  * Don't use capital letters or underscores for selector (class, id) names. Use dashes and lowerase.
  * Avoid inline styling, use classes instead.
```
.parent {
    font-weight: bold;
}
.parent .child {
    color: #FFFFFF;
}  

.next {
    color: #0000FF;
}
```

If you want to dive deeper, see https://cssguidelin.es/

## SCSS
We prefer to use SCSS over bare CSS. This enabled the following:
  * Use mixins to avoid repeating code, but take care to avoid the output CSS getting too large.
  * Define variables globally with brand colors.
  * Make modular files for each concern, and have SCSS combine them.

## Javascript, HTML and CSS Formatting

Use the Prettier autoformatter and standard. https://github.com/prettier/prettier

For projects using node, and supported editors (like VS Code) you can have a `.prettierrc.js` in your project root, like this.
```
{
      semi: false,
      singleQuote: true,
      tabWidth: 2
}

```

Alternatively, in VS Code, you can do `ctrl-,` to open settings, and search for "prettier". Scroll down to change the above settings manually.
