# Operations

This defines how we intend to set up, run and deploy project runtime environments.

## Docker

We use Docker to automate managing dev and prod environments. Specific conventions we follow:

  * It should be as easy and quick as possible to set up a new environment.
  * production and development environments should be as similar as possible (or, as practical anyway).
  * Base your Dockerfiles on official dockerhub.com images where they exist.
  * docker-compose.yml contains the Docker config which is the same between every environment.
  * A file called docker-compose.override.yml.template should exist with any settings that vary between environments. In a particular environment, to set up you would copy it and modify it locally. docker-compose.override.yml should be in `.gitignore`
  * The docker-compose.override.yml file should only contain differences between dev and prod and other environments. This includes the ports, restart policy, and normally not much else. If a line doesn't need to be in the overrides for a specific reason, move it to the main docker-compose.yml instead.

## Setting Up An Environment

1. [Install Docker on your machine](https://docs.docker.com/engine/installation/)

2. Copy the docker override template: `cp docker-compose.override.yml.template docker-compose.override.yml`

3. Run docker-compose: `docker-compose up`

4. Navigate to http://localhost.

5. If you want to use a different port on the host, such as when you want to run environments on the same host, map that in docker-compose.override.yml

```
services:
  web:
    ports:
      -9000:80
```

And visit http://localhost:9000

### Databases

We use postgres and occasionally mongodb. You can restore a postgres DB in our projects as follows. Include this portion `-T template_postgis ` if you have a postgis (as opposed to plain postgres) db image in your docker definitions. You may need to stop your other containers to abort their connections to the db first.

```
docker cp <sql filename> <project slug>_db_1:/tmp/
docker-compose exec db dropdb -U postgres postgres
docker-compose exec db createdb -U postgres [-T template_postgis ]postgres
docker-compose exec db psql -f /tmp/<sql filename> -U postgres postgres
```

Never expose the db management port, it should only be accessible via Docker.

#### Migrations

Migrations should be run as a part of a startup script, so the DB schema is always up to date with the currently running code.

Note: migration conflicts should be resolved when merging `develop` into your working branch and not as part of operations work.

## Backups
*ALL* production data of ours and clients' must be backed up. We must have reasonable evidence that backups can actually be restored. For example, periodically update your development environment's database using a backup from production.

Backups mostly go to S3 for projects we manage hosting for. To get a backup:

1. Ask your manager for an AWS IAM account.
2. Then, make yourself a token [here](https://console.aws.amazon.com/iam/home). Go to your username -> Security credentials -> Create access key .
3. To download a backup, you have to install [aws cli](https://docs.aws.amazon.com/cli/latest/userguide/installing.html). You'll be prompted for some information:
4. Enter your creds you generated in #2 above. The region is us-east-1.
5. Use the aws cli tools to get a backup.
```
aws s3 ls countable/backups/
aws s3 cp s3://countable/backups/<project>/<date>.tar.lrz .`
```

## Deploying Updates To Projects

While everything uses Docker as described above, every project is basically a unique unicorn in terms of hosting. We are moving projects to use Jenkins for CI, with 2 automated jobs.

1. Automatically test any change to the `develop` branch
2. Automatically deploy any change to the `master` branch

Generally, deploying involves updatnig the code from the known stable branch
```
git pull origin master
```

Restart the main application container, and ideally your migrations and staticfiles operations should be taken care of by an entrypoint script.
```
docker-compose exec restart web
```

Or, if a rebuild is needed.
```
docker-compose up --build web
```

Some projects use [Jenkins to automatically test and deploy new commits](./JENKINS.md).

### Static Files

nginx may as well always serve all static files in all environments. This prevents us needing to worry about differences in static file serving in various dev environments. To prevent the need to run `collectstatic` constantly in Django projects, static files should be served from a single directory, so that only 3rd party static files need collected. `python manage.py collectstatic --noprompt` should be run as part of the startup script for any Django project.

