
## Project Structure and Ops

ALL projects MUST:
  * Have a README.md file with all information and/or links required for a new person to run the project locally.
  * Be Dockerized, if they have more than a single service.
  * Not reference the production URL in code. Save this in the docker-compose.override.yml for the specific ENV.
  * Not save secrets in code. Save these in the specific docker-compose.override.yml for the specific ENV.

ALL projects SHOULD:
  * Use PORT 80 for http access in development environments.
  * Use our standard stack choices.
  
## Front End Development
 
  Front-end development is exciting, but also a challenge. This is due to the fact that there are so many tools available for   so many different things, and this side of the world moves fast. Main considerations:
  
  1. Browser compability - Does the website look good on Chrome? Firefox? Ipad? Galaxy? iPhone?
  2. Device compatibility (Responsive Design) - On monitors that are not 1080p? 10 inch laptops at 1280 x 720?
  3. Automation
  
   
  
Now a days, you don't necessarily need to CODE for this, since there are tools like Babel, Normalize.css, Autoprefixer which help make this happen.

On larger sites with an accessibility budget:

 4. WAI-ARIA (Web Accessbility Initiative)

TLDR: Your website needs to work on the browsers that the client needs them to work in. Countable's website should be a flawless experience in ALL platforms.

 **Tools**
 
Tooling for different areas can be in any of the following status:
  * Unspecified - Use whatever you want as long as it's well supported.
  * Recommendation - We recommend using a specific tool, but developer expertise or another reason could override this.
  * Standard - You should only deviate from this tooling choice for a specific reason.

  **CSS**
  
    Preprocessor: _Unspectified_ - We are evaluating SASS https://sass-lang.com/
    CSS Reset: _Unspecified_ - Use one though, as opposed to none.
    
    
  **MV\* Framework**
  
  I also believe using a framework such as React, Angular or what not reduces re-inventing the wheel. Also, front end projects using a framework is easier to maintain. Unless the website is small and does not require data flowing from back end to the front end, a usage of MV* framework is highly recommended. We currently do not have a framework of choice at the moment as of yet.
  
  1. React
  2. AngularJS
  3. Angular
  4. RiotJS
  5. Mithril JS
  6. Vue
  
  This list is in no particular order. Angular variants are the biggest in size which is a huge downside. Since we only leverage small portions of their features. In an enterprise application, it may make sense.
 
