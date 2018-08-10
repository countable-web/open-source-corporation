

ALl projects MUST:
  * Have a README.md file with all information and/or links required for a new person to run the project locally.
  * Be Dockerized, if they have more than a single service.
  * Not reference the production URL in code. Save this in the docker-compose.override.yml for the specific ENV.
  * Not save secrets in code. Save these in the specific docker-compose.override.yml for the specific ENV.

ALL projects SHOULD:
  * Use PORT 80 for http access in development environments.
  * Use our standard stack choices.
