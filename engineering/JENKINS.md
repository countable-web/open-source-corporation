

## What Does Jenkins Do?

  * Changes to `develop` (branch in bitbucket) are detected and Jenkins automatically runs our tests and notifies us in slack of status. If they pass they should be deployed to a staging area.
  * Changes to `master` are deployed to the production website.

## Setting up a new project.

  * Test that a fresh clone of your project works with `docker-compose up` and the tests pass.
  * Items in Jenkins (jobs) are named after their repository name. Each repo gets 2 items in jenkins. For a repo called <repo name>, the Jenkins items are <repo-name>-test and <repo-name>-deploy.
  * Create a new "item" and choose the option to clone an existing item called <repo name> and <repo name>-deploy.
  * Restrict the job to run on a specific node.
  * Change the repo URL and name of the item to match your repository.
  * Edit the job's commands to run your tests properly.
  * Configure slack to [post job status to the project's channel](https://github.com/jenkinsci/slack-plugin#install-instructions-for-slack).
 
## Prerequisites for the server

   1. Install packages
   Usually, Java, Git & Docker is enough.

   * Git
   ``
   sudo apt-get install git
   ``

   * Java
   ``
   sudo apt-get install default-jre
   ``

   * Docker
   ``
   https://github.com/countable-web/open-source-corporation/blob/master/engineering/OPERATIONS.md
   ``

## Setting up a Jenkins node & project

   1. Create a User
   ```
   adduser jenkins
   (enter his password)
   usermod -aG docker jenkins
   apt-get update
   apt-get install default-jre
   ```
   
   2. Create a Node
   In Jenkins, click Build Executor Status -> New Node.  Give this node a name and select Permanent Agent.
   The configuration required for a Node can be easily grabbed from previous Nodes. Refer back to these existing
   nodes to get a sense of what configuration is needed. This node is now what wil be used to deploy project of your choice.
   
   3. Create a Build Project
   In Jenkins, click new Item. Refer to existing projects for the configurations. 
   Make sure the node you just created is being used!

## Discussion on Usage of Jenkins

  * Jenkins is pretty great but also has a lot of shortcomings. The big one is you bury all this important config info in GUI menus instead of in a versionable place like code. Travis is better that way, but they're less flexible in some other ways.
  * If you find yourself building complicated scripts as Jenkins commands, instead script them into a bash file and just call that from Jenkins isntead.
