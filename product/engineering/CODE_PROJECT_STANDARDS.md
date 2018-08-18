
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
  
  1. Browser compability
  2. Device compatibility (Responsive Design)
  3. Automation
  
  Does the website look good on Chrome? Firefox? Vivaldi? Ipad? Galaxy? iPhone? Nokia? on monitors that are not 1080p?, Small resolution? 10 inch laptops?
  
Now a days, you don't necessarily need to CODE for this, since there are tools like Babel, Normalize.css, Autoprefixer which help make this happen. Those 3 tools have been at the core of every project that I have been involved in. And it doesn't have to be Babel or Normalize. Just something to automate and standardize your workflow for most browsers and devices out there. This is the first step towards launching a professional web page in my opinion.

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
    Reset: _Unspecified_ - Use one though, as opposed to none.
 
