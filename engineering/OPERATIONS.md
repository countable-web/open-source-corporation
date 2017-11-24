# Operations

## Docker

We use Docker to automate managing dev and prod environments. Specific conventions we follow:

  * It should be as easy and quick as possible to set up a new environment.
  * production and development environments should be as similar as possible (or, as practical anyway).
  * Base your Dockerfiles on official dockerhub.com images where they exist.
  * docker-compose.yml contains the Docker config which is the same between every environment.
  * A file called docker-compose.override.yml.template should exist with any settings that vary between environments. In a particular environment, to set up you would copy it and modify it locally. docker-compose.override.yml should be in `.gitignore`

## Setting Up An Environment

1. Install Docker on your machine. See this (link)[https://docs.docker.com/engine/installation/] to get started

2. Copy the docker override template: `cp docker-compose.override.yml.template docker-compose.override.yml`

3. Run docker-compose: `docker-compose up`

4. Navigate to http://localhost.

### Databases

We use postgres and occasionally mongodb. You can restore a postgres DB in our projects as follows. Include this portion `-T template_postgis ` if you have a postgis (as opposed to plain postgres) db image in your docker definitions. You may need to stop your other containers to abort their connections to the db first.

```
docker cp <sql filename> <project slug>_db_1:/tmp/
docker-compose exec db dropdb -U postgres postgres
docker-compose exec db createdb -U postgres [-T template_postgis ]postgres
docker-compose exec db psql -f /tmp/<sql filename> -U postgres postgres
```

Never expose the db management port, it should only be accessible via Docker.

## Backups
*ALL* production data of ours and clients' must be backed up. We must have reasonable evidence that backups can actually be restored. For example, periodically update your development environment's database using a backup from production.

## Deployment

While everything uses Docker as described above, every project is basically a unique unicorn in terms of hosting. There is an intent to at least standardize a CI solution, possibly Jenkins. Only one project currently has this set up.

Generally, deploying involves updatnig the code from the known stable branch
```
git pull origin master
```

Restart the main application container, and ideally your migrations and staticfiles operations should be taken care of by an entrypoint script.
```
docker-compose exec restart web
```

