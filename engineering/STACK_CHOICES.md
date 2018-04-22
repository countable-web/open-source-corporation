# Stack Choices

This page captures our current thoughts on the outlook for dependencies in our projects.

## JS Frameworks

| Technology    | Current | Ideal    |
| ------------- | ------- | -------- |
| jQuery | used in some   | avoid, slowly migrate to native dom |
| React  | not used       | avoid, prefer preact |
| Angular | used in some  | avoid, continue in existng usage |
| Riot   | used in some   | preferred for Django projects |
| Vue    | not used       | preferred for SPA projects |

## CSS

| Technology    | Current | Ideal    |
| ------------- | ------- | -------- |
| preprocessors (less/sass/stylus) | used rarely  | avoid, slowly migrate away |
| postCSS       | not used | preferred for complex css needs |
| CSS vars / scopes | not used | preferred |

## Django modules

| Technology    | Current | Ideal    |
| ------------- | ------- | -------- |
| celery | not used   | avoid, use django_rq |
