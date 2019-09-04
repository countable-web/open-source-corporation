# Servers

## Purpose

Improve consistency between our servers and establish best practices for deployment.

## Scope

Standardize setting up new servers. These steps are generic to AWS, Digital Ocean, and Scaleway currently. 

## Process.

### Providers

To choose a hosting provider.
1. Determine if the client is providing servers. If so, work with them to accomodate their process and needs.
2. If we are providing servers, and there are special needs only provided by AWS, use them (ie, Cognito or RDS).
3. Otherwise, if the server must be in Canada, use Digital Ocean (Toronto region)
4. If there are no restrictions, use Scaleway.

### Node Creation

  * For Digital Ocean, choose "create->Droplet".
  * Choose the latest LTS Ubuntu as the OS.
  * Choose an amount of RAM and Disk space by consulting the developers of the system you are installing. For a Django application with low traffic (under 1000 visits/day, and no special compute tasks like video transcoding) 2GB of RAM is ok. For most systems about 50GB of disk space is recommended.
  * Choose a name for the node that uses the project slug, ie `cortico` as the name. If the Node is only used in a subset of cases, indicate that, ie `cortico-clientname`.

### Bootstrapping
  
  * Log in as root (or ec2-user on AWS), and create a user for yourself in the `sudo` and `dev` groups.

```
ssh root@IP.ADDRESS
adduser myname
usermod -aG dev myname
usermod -aG sudo myname
```

  * Install [dotfiles](https://github.com/countable-web/dotfiles)
  * Set up [Jenkins](./JENKINS.md) if needed.
  * Create an account for any team member who needs access, and add them to the `dev` `sudo` and `docker` groups.
  
 Run your jenkins job to test the software works.
 
 ### Future Work
 
   * This process should be replaced with an IAS solution (Terraform + Ansible for example)