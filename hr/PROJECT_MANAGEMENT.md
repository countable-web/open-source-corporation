# Project Management

This document summarizes project management tooling and practices at Countable to assist with onboarding.

### GIT

We follow the [git-flow](https://datasift.github.io/gitflow/IntroducingGitFlow.html) branching conventions loosely. All projects should have a master (production) branch which releases are made from, and a develop (stable) branch for developers as a foundation to build features on. Feature branches are created from develop and merged back in via pull request when ready. Here are some [examples](./GIT.md) of how we'd use GIT in different cases.

### Jira

Some clients have Jira, and we use their system in this case. If they don't have Jira, we use Trello.

### Trello

We use Trello for project management, as it allows unlimited access to boards by partners and clients, encouraging more collaboration and transparency. See the next section for an explanation of our Trello board conventions.

#### Trello Board Headers

  * *Defer* - this column stores requested items that have been reviewed by the consultant but can't be worked on for some reason. Usually the item is unclear or conflicts somehow.
  * *Requests* - items the client has reqeusted that are not reviewed by the team yet. This is the starting point for the consultant to add items.
  * *Backlog* - items that have been understood by the consultant, and could be worked on. This is the traditional Scrum backlog list, ordered by priority (highest on top)
  * *Sprint (In Progress)* - items actively being worked on in the current week.
  * *Done* - items that are done and testable by the client (and where not possible, the consultant). A test can take the form of a client approval, code review, or automated test written.

## Methodology

  * We use a loose agile project management methodology. This is a subset of Scrum.
  * Each client should have a priority ordered backlog (either in Trello or Jira)
  * We encourage active projects to engage in a monthly or biweekly sprint plan and retrospective. This meeting includes discussing what backlog was done, updating the order of the backlog, and raising any problems for the team to address in order to improve our work velocity.

