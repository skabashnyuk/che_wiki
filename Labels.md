## Issue Labels
The Eclipse Che project relies heavily on [issue labels](https://github.com/eclipse/che/labels) as a way to communicate status and responsibility.

### Issues and pull request for new contributors
The following labels will appear in the https://github.com/eclipse/che/contribute page.

| Label        | Description
| ------------ |-------------
| `good first issue`| Community, this issue looks easy to start with for a new contributor. Just take it. We'll help you!
| `help wanted`| Community, our teams are fully engaged on other issues. Feel free to take this one. We'll help you!


### Issue Types
| Label        | Description
| ------------ |-------------
| `kind/question`| Questions that haven't been identified as being feature requests or bugs.
| `kind/enhancement`| A feature request - must adhere to the feature request template.
| `kind/epic`| A long-lived, PM-driven feature request. Must include a checklist of items that must be completed, which can reference enhancements or bugs.
| `kind/bug`| Outline of a bug - must adhere to the bug report template. If a bug is identified during a question investigation a new issue can be created for the bug and the question closed.
| `kind/task`| Internal things, technical debt, and to-do tasks to be performed.
| `kind/docs`| A work item tied to documentation.
| `kind/planning`| A checklist of issues that a team is planning for a particular sprint.
| `kind/usability`| Issues related to the end-user experience.
||
| **Bug Severities**| _________________________________________________________________________ |
| `severity/blocker`| Causes system to crash and be non-recoverable or prevents Che developers from working on Che code.  Must be resolved immediately. Can only be applied to `kind/bugs`.
| `severity/P1`| Has a major impact to usage or development of the system. Issues / PRs with P1 status should be prioritized during sprint planning. Can be applied to all kinds of issues. Not all issues need a severity. If an enhancement or bug will take >1 sprint to address consider using the `roadmap/*` labels instead.
| `severity/P2`| Has a minor but important impact to the usage or development of the system. Should be considered when planning sprints. Can be applied to all kinds of issues. Not all issues need a severity. If an enhancement or bug will take >1 sprint to address consider using the `roadmap/*` labels instead.
||
| **Issue Level**| _________________________________________________________________________ |
| `level/beginner` | A relatively easy issue that's well suited to being addressed by a pull request from the community.
| `level/intermediate` | A more advanced issue that is open to a pull request from a community member with more experience in Che.
| `level/advanced` | A challenging issue that is complicated and needs help from a community member with domain experience.
||
| **Dev Open Issue Status**| _________________________________________________________________________ |
| `status/info-needed` | More information is needed before the issue can move into the “analyzing” state for engineering.
| `status/analyzing` | An issue has been proposed and it is currently being analyzed for effort and implementation approach.
| `status/open-for-dev` | An issue has had its specification reviewed and confirmed. Waiting for an engineer to accept the issue and take it into active development.
| `status/in-progress` | This issue has been taken by an engineer and is under active development.
| `status/code-review` | This issue has a pull request posted for it and is awaiting code review completion by the community.
| `status/pending-merge` | This issue has completed development and awaiting authorization to be merged into master. Sometimes issues can be completed, but are placed on hold to merge in "info-needed", "analyzing", "open-for-dev", "in-progress", "code-review" or "blocked". Issues with a `pending-merge` label need to reference the PR(s) that are pending.
| `status/blocked` | Issue that can’t be moved forward. Must include a comment on the reason for the blockage. If it’s blocked because it depends on another issue then it should include a link to the issue it depends on.
||
| **Dev Open Pull Request Status**| _________________________________________________________________________ |
| `status/work-in-progress` | This PR is not ready to be merged. There is additional testing, development or input required.
| `status/merge-ready` | All reviews have been finalized. The PR can be merged into master if merges are being accepted according to sprint or milestone plan.
||
| **Roadmap labels**| _________________________________________________________________________ |
| `roadmap/this-QTR` | A large scale feature or bug fix that is scheduled to be addressed in the current quarter.
| `roadmap/next-QTR` | A large scale feature or bug fix that is scheduled to be addressed in the next quarter.
||
| **Sprint labels**| _________________________________________________________________________ |
| `sprint/current-sprint` | Issue is being worked in the current sprint.
| `sprint/next-sprint` | Issue is planned to be worked in the next sprint.
||
| **Team Assignments**| _________________________________________________________________________ |
| `team/ide` | Issue to be taken by the IDE team.
| `team/enterprise` | Issue to be taken by the enterprise features team.
| `team/osio` | Issue to be taken by the OpenShift.IO team (working on the integration of Che in OpenShift.IO).
| `team/plugin` | Issue to be taken by the plugin development team.
| `team/production` | Issue to be taken by the production readiness team.
| `team/platform` | Issue to be taken by the platform team.
| `team/pm` | Issue to be taken by the product management team.
| **Pull Request Target**| _________________________________________________________________________ |
| `target/branch` | Indicates that a PR will be merged into a branch other than master. When merging to master branch `target/` label should not be used as it is an assume default target for most PRs.
| `target/che5` | Indicates that a PR or an issue will be merged into che5. 
| `target/che6` | Indicates that a PR or an issue will be merged into che6 branch. 