# Operations

This defines how we intend to manage web technology project environments. High level goals:

  * Subscribe to the [12 factor methodology](https://12factor.net/)
  * Automate operations to make our work more efficient, secure, consistent, predictable and reliable.
  * When something breaks, make it as transparent as possible (easy to see what happened)
  * When something breaks, find the root cause and prevent it next time.
  * Save as much time for developers as possible, by automating their deployments, dev env setup, and testing.
  * Eliminate unnecessary differences between projects, and have everything follow convention when there's no reason for deviations.
  * Reduce and simplify the steps needed to start a new project and integrate with everything (slack, jenkins, sentry)
  * minimize what's on the host server. Dockerize it all so it can be tested fully locally, and host as minimal state. ie, backup jobs are currently done wrong as they use the host's CRON.


## More specific goals (draft, may change)

  * It would be ideal to bring up a project environment with one short command. (currently, it's `git clone <repo>`, `docker-compose up`, and then you often need to get some test data so 2 or more commands, which is a good start). The easier this is, the more our front end people will be able to work the same way as everyone else.
  * Committing to the master branch should run tests, and if those succeed, deploy to production.
  * Committing to develop should deploy to a staging environment, and run the tests, spamming the comitter of any errors.
  * All deployment configs should be centralized in the source repository. (ie, `dc.prod.yml`, `dc.stage.yml`)
  * Sentry.countable.ca should have a project for every production environment, and spam slack with any errors.
  * TODO: It should be fully automated to create a new jenkins slave server.

## Current Standards and Conventions

### Servers

Each client typically has a different server environment, and Docker mostly prevents us from caring about the differences.

### Jenkins

See [here](./JENKINS.md) for how we use jenkins to automate many environment instances.

### Docker

See [here](./DOCKER.md) for how we use Docker to manage project environments.

### Cloudflare

We use cloudflare as an SSL proxy and DNS server. Your project should have an A record for its primary domain `project.com` which is proxied through Cloudflare's CDN. You should have a second CNAME record which is NOT proxied for directly accessing the server. `direct.project.com` .

## Backups
*ALL* production data of ours and clients' must be backed up. We must have reasonable evidence that backups can actually be restored. For example, periodically update your development environment's database using a backup from production.

Backups mostly go to S3 for projects we manage hosting for. To get a backup:

1. Ask your manager for an AWS IAM account. Sign in here: https://413528927365.signin.aws.amazon.com/console/ using your new credentials.
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

Mac OSX:
(assumes you already have [brew](https://brew.sh/) installed)
```
brew install lrzip
lrzip -d $filename
```

### Servers

Go [here](./SERVERS.md) to learn how to deploy a new node.

### Databases

We use postgres and occasionally mongodb. You can restore a postgres DB in our projects as follows. Include this portion `-T template_postgis ` if you have a postgis (as opposed to plain postgres) db image in your docker definitions. You may need to stop your other containers to abort their connections to the db first.

```
docker cp <sql filename> <project slug>_db_1:/tmp/
docker-compose exec db dropdb -U postgres postgres
docker-compose exec db createdb -U postgres [-T template_postgis postgres
docker-compose exec db psql -f /tmp/<sql filename> -U postgres postgres
```

Never expose the db management port, it should only be accessible via Docker.

#### Migrations

Migrations should be run as a part of a startup script, so the DB schema is always up to date with the currently running code.

Note: migration conflicts should be resolved when merging `develop` into your working branch and not as part of operations work.

## Deploying Updates To Projects

While everything uses Docker as described above, every project is basically a unique unicorn in terms of hosting. We use Jenkins for CI, with 3 automated jobs.

1. Automatically test any change to the `develop` branch
2. Automatically deploy any change to the `master` branch
3. Automatically run tests on any change to `develop` branch.

Generally, deploying involves updating the code from the known stable branch
```
git checkout master
git merge develop
git push origin master
```


Some projects use [Jenkins to automatically test and deploy new commits](./JENKINS.md).

### Static Files

An nginx container may as well always serve all static files in all environments. This prevents us needing to worry about differences in static file serving in various dev environments. To prevent the need to run `collectstatic` constantly in Django projects, static files should be served from a single directory, so that only 3rd party static files need collected. `python manage.py collectstatic --noprompt` should be run as part of the startup script for any Django project.


### Moving sites to a new server

Move the "stage" version of any site, first.

1. Update the jenkins job to point to the new node. Run it, and test the site runs on its custom HTTP port (used by the nginx/haproxy on that node).

The following steps should be done as quickly as possible because your service will be down in between these steps. Test the process on the stage instance to ensure it goes smoothly first. It should only take a few minutes.
1. Set the old instance database in read-only mode if possible. For small sites, skip this step, and just shut it down at this time, resulting in some downtime.
1. Dump the database from the old instance, and restore it to the new instance.
1. Update DNS to point to the new instance.
1. Update the proxy of the old site to point to the new one to avoid clients with old DNS records accessing the old version, because it could result in DB conflicts or data loss.
1. Turn off the old service on the old server, to guarantee it cannot be accessed.

For some legacy sites, we store local filesystem data. This must be moved manually to match the old server, on the new server. Ask the devs to refactor this away where possible, and use things like S3 for permanent file storage.
