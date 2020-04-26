# Trello

## Purpose
We use Trello for project management, as it's simple to set up access to the appropriate boards by partners and clients. A Trello board consists of a set of [Cards](#trello-cards) (tasks) arranged in [Columns](#trello-board-columns).

## Scope
Define how Countable uses Trello to manage our Scrum backlog. [See video version](https://www.youtube.com/watch?v=6X9x4SCLhKs).

### Trello Cards

A card should contain a clear description of work to be done by one person required to support a given [User Story](https://github.com/countable-web/open-source-corporation/blob/master/peopleops/getting_started/USER_STORIES.md). This may correspond to a single User Acceptance Test. A card should typically be between 1 hour and 1 day of work. If it's longer, split it into 2 cards in that column.

### Trello Board Columns

#### Ideas
Stuff that's not clear enough to be in backlog yet.

#### Requests
This is the starting point for anyone to add cards, and where cards the client has requested live until the Scrum Master can review and ensure they're actionable and clear. 

If they're actionable, move them to Backlog. If they're not, write a comment to the client asking for more information in order to make it actionable, and leave it in the deferred column. 

If any additional requirements steps such as a mockup are required, mention that in the card. Attach any additional examples and/or specifications to the card.

#### Feedback
On this column, we may store cards that somehow need client or manager review before proceeding further. In practical terms, we use this section whenever we need some client data or feedback to progress with our current task.

#### Backlog
Cards that are clear and actionable, and have an estimated impact and effort associated with them. This is the traditional Scrum backlog list, ordered by priority (highest on top), by the Product Owner. 

There is only one backlog column, because we need to use the current sprint's lessons to plan future sprints. So, we cannot plan future sprints in advance, we can only set card priority.

#### Sprint
Cards actively being worked on in the current week.

#### Done
Cards that are ready to be tested by the client (and when that's not possible, by the consultant). A test can take the form of a client approval, code review, or automated test written.

### Moving cards between columns

A diagram shows how cards can move from conception to completion [here](https://drive.google.com/open?id=1VrniT1lRqVu9sJr0ZMK1aQLnFwEuFIQD). As the diagram illustrates, each column corresponds to a specific within the adapted SCRUM(https://github.com/countable-web/open-source-corporation/blob/master/peopleops/getting_started/SCRUM.md) framework.

### Progress Awareness

**It's essential to keep our clients informed about our current progress** on particular tasks, so our professional relationship is strengthened and trust is built. For this objective, we suggest that you:
1) Take screenshots of finished progress (when applicable) and post on your trello ticket.
2) Use checklists for keeping track of what's being done.
3) Use "Screencastify" chrome extension for recording short screencasts and attaching into your trello ticket

### The "critical" label

If you find something that's severly broken in any of our websites, please create a Trello card with a red label `critical`, and tell the developer who you've assigned it to. Do this sparingly: only when it's something we're likely to quickly lose customers over such as a service being down completely or a button not working. For less serious bugs, don't use this label, just make a regular card.

### Boards

We typically have one board per codebase with a client, and one per internal product / project. The board background color indicates the following:
  * Green - nonprofit client (private)
  * Orange - corporate client (private)
  * Red - internal operations (private)
  * Purple - open source project, or other public board (public)
  * Blue - internal product (private)

### Getting everything into Trello

Clients will often email you rather than use Trello. This can be fixed by forwarding their email to the Trello board. 

Go to their Trello board, and click settings -> email-to-board settings, and add that email address as a contact in your email. You can then forward emails directly to your trello board. 

However, it does make a bit of a mess since email signature images and other junk show up in the tickets, so it's nice to clean them up when you look at them in Trello.

### Effort vs Impact Tags

You'll note that some cards will present a effort vs impact tag to assist us in our task prioritizing. You can check more information at:  [EFFORT vs IMPACT](../../admin/performance/EFFORT_IMPACT.md)


