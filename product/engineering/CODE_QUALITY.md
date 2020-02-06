# Code Quality

Tested tricks for having good code you like to work on in the long term.

  * Assume you’ll still be working on any project 10 years from now, and cultivate a culture with a long-term viewpoint. We hire for this trait and use code reviews as well as weekly developer training workshops to improve maintainability together. This seems expensive but has paid enormous dividends in reduced technical debt.  Reviewers have fresh eyes and can see what’s missing more easily than the original developer. These discussions form an evolving standard and reinforce a culture of quality and continuous learning.
  * Decouple core business logic from framework-specific code and views. Code that is close to the presentation layer will be forced by front-end libraries, web browsers and marketing needs to evolve quickly.
  * Auto-formatters. We prefer code standards which have an auto-formatter because it lets makes our code perfectly consistent at a syntax level with zero effort.
  * Document rationale. Comments should answer “why” code was written a certain way. The code itself should document “what” it is.
  * Use “TODO” comments to document future intent of the code.
  * Code reviews - for learning and establishing standards. The code reviews become a living history of the project’s standards. While standards should be documented in one place concisely, it’s in the code reviews that all the small subtleties will be discovered. The reviewer can ask the question “would I like reading this code and having to modify it myself?” since they have fresh eyes. They can see what’s missing more easily than the original developer. These discussions lead to an evolving standard, and a culture of quality and continuous learning.
  * Declarative Style - Anything you do a lot of should be *declarative style* to the extent possible (as opposed to imperative style), meaning define what you want and not the order it is created.

Consistency and quality can be further improved by proactively managing technical debt. While we do avoid needless technical debt, it can be taken on strategically. For example, prototyping a solution can be a cheap way to get information and save cost overall, as long as you don’t neglect to refactor or rewrite the prototype if you decide to keep the code.
