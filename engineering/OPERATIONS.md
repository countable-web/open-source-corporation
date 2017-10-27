# Operations

## Docker

We use Docker to automate managing dev and prod environments. Specific conventions we follow:

  * It should be as easy and quick as possible to set up a new environment.
  * production and development environments should be as similar as possible (or, as practical anyway).
  * Base your Dockerfiles on official dockerhub.com images where they exist.
  * docker-compose.yml contains the Docker config which is the same between every environment.
  * A file called docker-compose.override.yml.template should exist with any settings that vary between environments. In a particular environment, it is copied as docker-compose.override.yml should be in `.gitignore`
 
