
# Engineering Reference

The purpose of this section is to standardize key (not all) engineering processes in order to improve the team's performance, and take advantage of an experience curve by eliminating arbitrary process differences.

## Approach

This is how we build things.

  * Build a prototype first to validate everything (market, feasibility, usefulness). It's encouraged to take shortcuts as long as your project is just a prototype and not used in production.
  * When a prototype is validated, it transitions to a product and must be made maintainable.
  * When working on existing projects (products), always leave things in a little better state than you found it.

## Stack Choices

We don't want to support every stack, so we chose the best for most cases and want to pass on the benefits of a superior stack to our clients, rather than them making an uninformed choice. Our stack selection is based on the following (descending importance):

1. Popularity, growth, longevity and community support.
2. Power, generality, flexiblity and interoperability.
3. Open Source, inclusive community.
4. Ease of use, readability, simplicity.
5. Performance.

We've found the following stack to be very good on these metrics.

  * Python - 3rd most loved language, and is the most wanted. [1]
  * Node.js - 4 most loved language, 2nd most wanted. [1]
  * Django / Flask / Express
  * Unix (Ubuntu Linux for servers)
  * PostgreSQL - 2nd most loved database [1]
  * Redis - most loved database [1]
  * Docker

[1] [Stack overflow dev survey](https://insights.stackoverflow.com/survey/2018/?utm_source=Iterable&utm_medium=email&utm_campaign=dev-survey-2018-promotion)

Python in particular is a very strong general purpose stack choice. With "software eating the world", Python's been the condiment of choice, and is appearing in many niche industries. This lets us synergize with other of our clients' projects, staff and expertise within the same lingua franca.

![python popularity](https://zgab33vy595fw5zq-zippykid.netdna-ssl.com/wp-content/uploads/2017/09/growth_major_languages-1-1024x878.png)

### Follow 12 factor principles

These are progressive principles for making your application predictable and scalable.

https://12factor.net/

### Front end

We have a lot less prescription on the front end, and choices are based on developer skill. However, we observe guidelines:

  * Bias towards fewer dependencies. What's the simplest set of dependencies that will work?
  * Bias towards small, specific purpose dependencies over frameworks. React, Preact and Riot is better than Angular in this way, for example.
  * Ensure depedencies have healthy community support and/or are small enough to fork if support wavers. Ideally both.


## Operations Manuals For Engineering

  * [Coding Standards](./CODING_STANDARDS.md)
  * [Ops](./OPERATIONS.md)
