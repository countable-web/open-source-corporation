

## What Does Jenkins Do?

  * Changes to `develop` (branch in bitbucket) are detected and Jenkins automatically runs our tests and notifies us in slack of status.
  * Changes to `master` are deployed to the production website.

## Setting up a new project.

  * Test that a fresh clone of your project works with `docker-compose up` and the tests pass.
  * Items are named after their repository name. Clone an existing item called <repo name> in Jenkins
  * Change the repo URL and name of the item to match your repository.
  * Do the same for the job named <repo name>-deploy.
  * Edit the job's commands to run your tests properly.
  * Configure slack to [post job status to the project's channel](https://github.com/jenkinsci/slack-plugin#install-instructions-for-slack).
