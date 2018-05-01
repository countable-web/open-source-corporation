# Operations

This defines how we intend to manage web technology project environments. High level goals:

  * Subscribe to the [12 factor methodology](https://12factor.net/)
  * Automate operations to make our work more efficient, secure, consistent, predictable and reliable.
  * When something breaks, make it as transparent as possible (easy to see what happened)
  * Save as much time for developers as possible, by automating their deployments, dev env setup, and testing.
  * Eliminate unnecessary differences between projects, and have everything follow convention when there's no reason for deviations.
  * Reduce and simplify the steps needed to start a new project and integrate with everything (slack, jenkins, sentry)

## More specific goals (draft, may change)

  * It would be ideal to bring up a project environment with one short command. (currently, it's `git clone <repo>`, `docker-compose up`, and then you often need to get some test data so 2 or more commands, which is a good start). The easier this is, the more our front end people will be able to work the same way as everyone else.
  * Committing to the master branch should run tests, and if those succeed, deploy to production.
  * Committing to develop should deploy to a staging environment, and run the tests, spamming the comitter of any errors.
  * All deployment configs should be centralized, possibly in the source repo (jenkins breaks this).
  * Sentry.countable.ca should have a project for every production environment. This already works fairly well.
  * Educate the team on linux/unix operating systems and concepts (and even their philolsophy)
  * Document and template the setup of a new project so it's mostly automated.

## Current Standards and Conventions

### Jenkins

See [here](./JENKINS.md) for how we use jenkins to automate many environment instances.

### Docker

See [here](./DOCKER.md) for how we use Docker to manage project environments.

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
aws s3 cp s3://countable/backups/<project>/<date>.tar.lrz .
```
6. Backups are archived with lrzip, so you'll have to install that (or 7zip)

Ubuntu:
```
sudo apt-get install lrzip
lrzip -d $filename
```

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

An nginx container may as well always serve all static files in all environments. This prevents us needing to worry about differences in static file serving in various dev environments. To prevent the need to run `collectstatic` constantly in Django projects, static files should be served from a single directory, so that only 3rd party static files need collected. `python manage.py collectstatic --noprompt` should be run as part of the startup script for any Django project.

