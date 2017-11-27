

## What Does Jenkins Do?

  * Changes to `develop` (branch in bitbucket) are detected and Jenkins automatically runs our tests and notifies us in slack of status.
  * Changes to `master` are deployed to the production website.

## Setting up a new project.

  * Test that a fresh clone of your project works with `docker-compose up` and the tests pass.
  * Items in Jenkins (jobs) are named after their repository name. Each repo gets 2 items in jenkins. For a repo called <repo name>, the Jenkins items are <repo-name>-test and <repo-name>-deploy.
  * Create a new "item" and choose the option to clone an existing item called <repo name> and <repo name>-deploy.
  * Change the repo URL and name of the item to match your repository.
  * Edit the job's commands to run your tests properly.
  * Configure slack to [post job status to the project's channel](https://github.com/jenkinsci/slack-plugin#install-instructions-for-slack).
