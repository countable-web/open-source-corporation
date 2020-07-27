This page is archived. Please visit [https://countable-ops-manual.readthedocs.io/](https://countable-ops-manual.readthedocs.io/)
# Python

## Purpose

Capture things that are useful to know when working on Python codebases at Countable.

## Scope

Patterns of problems that come up fairly often as a developer, and guidance for those.


## Debugging Python

Basics:
  * You should become familiar with Python's debugger, `pdb` . Here are a few common cases with recipes.
  * If you want to inspect any object (variable) in python, use the `dir(obj)` function in the python CLI (>>>)
  * If you want to know the source file of any module, do `import module` and then `module.__file__`

### There is a trace in Library code and you want to look around

1. Look at the stack trace, and identify the file and line you want to break at.
2. Add `import pdb; pdb.set_trace()` on that line and save the file.
1. Run your program, and when that line is reached the debugger will start interactively in your terminal.


### The program is really unstable and you want to debug whenever it crashes.

1. Replace the executable `python` with `pdb` temporarily, in your Dockerfile or docker-compose.yml
1. For example, `python manage.py runserver` becomes `pdb manage.py runserver`
1. Now, restart your web (django) container in the foreground. ie) `docker-compose stop web && docker-compose up web`
1. When the program crashes, your terminal will halt in a PDB interface and you can print variable names, etc.
