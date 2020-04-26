

# Release Management

Each project may have some differences by the ideal release management process should aspire to these goals:

  * Allow developers to efficiently commit code knowing it will be tested all at once before release.
  * Implement automated end-to-end (puppeteer) testing of core user flows is first, then other tests as desired.
  * Be able to confidently release every sprint (every week usually).

Specific processes that help with the above:

  * Developers work on `feature-branch` named branches (see [GIT](./engineering/GIT.md)) and commit and push often. Atomic commits increase developer happiness by 10% according to the 2017 StackOverflow survey.
  * Developers take responsibility for cleaning up their code, testing, and then making a Pull Reqeust.
  * The pull request should be reviewed by a peer to adhere to our [code standards](./engineering/CODE_PROJECT_STANDARDS.md), ensure the code is readable and self-documenting, and to help us learn from each other.
  * When approved, anyone may merge the Pull Request into `develop` (never `master` directly)
  * The `develop` branch is automatically staged so we can review the product together and report any bugs prior to it being released.
  * Ideally once per week, `develop` is auto-merged into `master` which triggers a release.
  * Critical bugfixes may bypass the above process by pushing [hotfixes](./engineering/GIT.md) to `master`. Do this sparingly. 
  
