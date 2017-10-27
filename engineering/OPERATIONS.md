# Operations

## Docker

We use Docker to automate managing dev and prod environments. Specific conventions we follow:

  * It should be as easy and quick as possible to set up a new environment.
  * production and development environments should be as similar as possible (or, as practical anyway).
  * Base your Dockerfiles on official dockerhub.com images where they exist.
  * docker-compose.yml contains the Docker config which is the same between every environment.
  * A file called docker-compose.override.yml.template should exist with any settings that vary between environments. In a particular environment, it is copied as docker-compose.override.yml should be in `.gitignore`
 
## Deployment

While everything uses Docker as described above, Every project is basically a unique unicorn in terms of hosting, but the intent is to standardize a CI solution, possibly Jenkins. Only one project currently has this set up.

Generally, deploying involves updatnig the code from the known stable branch
```
git pull origin master
```

Update the code, and ideally your migrations and staticfiles operations should be taken care of by an entrypoint script.
```
docker-compose exec restart web
```
