

ALl projects MUST:
  * Have a README.md file with all information and/or links required for a new person to run the project locally.
  * Be Dockerized, if they have more than a single service.
  * Not reference the production URL in code. Save this in the docker-compose.override.yml for the specific ENV.
  * Not save secrets in code. Save these in the specific docker-compose.override.yml for the specific ENV.

ALL projects SHOULD:
  * Use PORT 80 for http access in development environments.
  * Use our standard stack choices.
  
  
 FRONT END DEVELOPMENT:
 
  Front-end development is exciting, but also a challenge. This is due to the fact that there are so many tools available for   so many different things. However, there are few key requirements for every front end project in my opinion. I (Aaron) always try to stay relevant since this side of the world moves fast. On every single project however, there are core requirements that  in my opinion should be taken care of for the sake of professionalism.
  
  1. Website compability.
  2. Responsive Design
  3. Automation
  
  Does the website look good on Chrome? Firefox? Vivaldi? Ipad? Galaxy? iPhone? Nokia? on monitors that are not 1080p?, Small resolution? 10 inch laptops?
  
Now a days, you don't necessarily need to CODE for this, since there are tools like Babel, Normalize.css, Autoprefixer which help make this happen. Those 3 tools have been at the core of every project that I have been involved in. And it doesn't have to be Babel or Normalize. Just something to automate and standardize your workflow for most browsers and devices out there. This is the first step towards launching a professional web page in my opinion.

If you go wrong here, it does not matter how good your website is, if you left out a portion of population because of your incompetence, then that is on you (At least this is the way I think). You can think of this as "web racism" (Haha). It's a different story if the client is OK with it, but if you use the tools, it doesn't matter if the client is okay with it or not, because it will work great anyway even on the things they don't have to support.

My two cents on how I believe the process should be. Not much of a operation guide. Feel free to edit.

By the way, you can take this a step further and also include

 4. WAI-ARIA (Web Accessbility Initiative)
 
But usually this is a very specific domain, or you are a very large website, like google.
