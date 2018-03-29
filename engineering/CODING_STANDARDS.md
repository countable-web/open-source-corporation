# Coding Standards

Coding and other standards and practices at Countable Web Productions.
  * This document has arisen out of specific cases where different conventions of developers have caused us to waste time. In some cases, standardizing won't give us this benefit so we won't do it. I currently think double versus single qutoes for strings is such a case.
  * There will be cases where we disagree, but we must all agree that it's more important to be consistent than to follow a particular rule. So, some rules may be arbitrary or even suboptimal, but we follow them so we can stop thinking about them.
  * Coding standards are only necessary when there are multiple ways to express the same logic (more than one program has the same behaviour). In this sense, they're very uninteresting and ideally would be fully automated away. Golang does this correctly by automating formatting as a core feature. This ideal is what we should aspire to so we can save our neurons for more interesting things. To this end, please use editor plugins that auto-format to our standards where possible.
  * In the case a project doesn't currently follow our standards but follows a different one, stick with that project's conventions unless we make a conscious decision to refactor the whole thing. Don't mix conventions.

### Principles

  * Make life easier for your team mates and future self by being consistent and thoughtful of what someone unfamiliar would think.
  * The perfect implementation is the one which declaratively encodes the business domain. If code becomes non-trivial, re-write so that domain is expressed in declarative form.
  * [Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance)

### Names

  This section refers to the names of variables, database columns, classes, and any other case where a name is chosen in code.

  * Names should be the most obvious thing possible (as opposed to clever or arbitrary).
  * Name length should be proportional to the variable's scope size. `x` is ok in a one liner, but not a global.
  * When an industry jargon (domain language) term is available, use that.
  * ClassNames - Classes should use an upper camel case string of nouns
  * attributes_names - Attributes (and local variables) should use lowercase with underscores
  * CONSTANT_NAMES - Constants should be uppercase with underscores.

### Files

  * Filenames should be lowercase with dashes (NOT SPACES) to separate words.
  * The purpose, and contents of any file should be as obvious as possible by its filename and location.

### Locality

Functional Modules
  * Modules should be responsible for a specific task or set of RELATED tasks.
  * Modules should communicate through easily testable interfaces. A huge heirarchy of objects shouldn't be required to test a single method, because the method should only take arguments it actually uses (not a big tree which happens to contain those)

### Comments
  
  * Do not comment what is obvious from the code. "# Increment the variable." is not a good comment.
  * Do Document the rationale "why", the reason behind an implementation choice.
  * Comment beside anything that's unintutive or unexpected to another reader.


### No tabs

We are a Python shop, and so observance of pep 8 leads us to use 4 spaces for indentation. We carry this convention to other languages, using 4 spaces for indentation in CSS, HTML, Javacript, etc. We never use the tab character.

### Docker

Please use Docker for any web application project (and other projects where applicable). It should be possible to bring up a new environment by only the following for any of our projects.

```
git clone <repo>
cd <project folder>
cp docker-compose.override.yml.template docker-compose.override.yml
docker-compose up
```

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

Opening and closing tag should have same indentation level, or on the same line. Use 2 spaces per indent level.
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

  * Break the styles into global.css (styles on all pages), layout.css (outer styles), pages.css (specific page and shared components)
  * Rules should generally pass on http://csslint.net/
  * Don't use !important when possible
  * Don't use capital letters or underscores. Use dashes and lowerase.
  * Indent scoped rules relative to parents (see below)

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
 
## Javascript Coding Standards

For javascript, use the Prettier autoformatter and standard. https://github.com/prettier/prettier
