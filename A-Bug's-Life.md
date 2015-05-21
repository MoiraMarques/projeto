**Github Issues:**

* We are (mostly) using a milestone-free model
* In some cases a larger body of work may be put into a specific milestone so that it's individual tickets can be worked off a singular list.  A meta ticket pointing to the milestone tickets should remain in the main list tagged with it's priority.
* Each ticket should be able to be tested independent of any other ticket and considered safe to deploy once the verification process is completed.

**Starting a ticket:**

* Tickets should be worked off in order of priority, (*blocker, critical, important*) as tagged in the bug list.
* Dev assigns the issue self and changes the label to *in-progress*
* Dev makes a new github branch (off of staging branch) named for the particular issue, (ex. gh-483).
* Once branch is initially pushed to github, QA can initiate testing / verification process.

**Verifying a ticket:**

* QA manually checks the branch changes either locally or on the demo instance
 * Demo instances are launched via jenkins https://builder.amara.org/ preview build job.
* QA runs the selenium test suite (either locally or via jenkins)
* QA updates or creates any relevant selenium tests
* QA pushes any test changes to the branch
* If there are failures (major errors, regressions ...):
 * QA notifies Developer either via ticket / irc, email, 
 * Dev resumes work on the ticket
* If additional bugs are found that are minor, a new ticket can be created for that particular issue if it need not block the current issue.  It should be referenced in the original ticket.
* If everything is good with the ticket:
 * QA creates a pull-request for the branch
 * QA notes in the pull request if a migration is required

**Merging the ticket:**

* 2nd Developer reviews the pull request
 * if issues makes comments and collaborates with original developer
 * if OK - merges the request to the staging branch
* Selenium tests are run automatically against staging branch via jenkins on commit.
* With successful test completing staging server is deployed.

**Deployment:**
* Any time tests against staging branch are all passing staging is considered safe to deploy
* On agreement between QA, Dev, Dev-Ops, productions deployment process starts
* If migration is required:
 * Dev determines if downtime is required for a safe deployment
 * PM notifies amara team, partners, translation team managers... of impending downtime
* Dev team deploys production, and notifies team when complete
* PM sends a notification to team, partners of deployed changes.
* PM closes the list of deployed tickets and generates release notes.


