## Issue Labels
The Eclipse Che project relies heavily on issue labels as a way to communicate status and responsibility.

### Issue Types
| Label        | Description
| ------------ |-------------
| kind/question | Questions that haven’t been identified as being feature requests or bugs.  Cannot overlap with “enhancement”, “bug”, “epic”, “task” or “docs”.
| kind/enhancement | A feature request - must adhere to the feature request template. Cannot overlap with “question”, “bug”, “epic”, “task” or “docs”.
| kind/epic | A long-lived, PM-driven feature request. Must include a checklist of items that must be completed, which can reference enhancements or bugs.  Cannot overlap with “question”, “enhancement”, “bug”, “task” or “docs”.
| kind/bug | Outline of a bug - must adhere to the bug report template. If a bug is identified during a question investigation a new issue can be created for the bug and the question closed. Cannot overlap with “question”, “enhancement”, “epic”, “task” or “docs”.
| kind/task | Internal things, technical debt, and to-do tasks to be performed. Cannot overlap with “question”, “enhancement”, “bug”, “epic” or “docs”.
| kind/docs | A work item tied to documentation.  Cannot overlap with “question”, “enhancement”, “bug”, “epic” or “task”.
| kind/planning | A work item outlining a part of our planning process - for example milestone overview issues is labelled with this.
### Bug Severities
| Label        | Description
| ------------ |-------------
| severity/blocker | Causes outage or prevents a fundamental feature from operating against its specification.  Must be resolved immediately. Bugs can only be labelled blocker if they are assigned to a milestone. Bugs that are not blockers do not need a severity.
### Dev Open Issue Status
| Label        | Description
| ------------ |-------------
| status/info-needed | More information is needed before the issue can move into the “analyzing” state for engineering. Cannot overlap with “analyzing”, “open-for-dev”, “in-progress”, “code-review”, “pending-merge” or “blocked”.
| status/analyzing | An issue has been proposed and it is currently being analyzed for effort and implementation approach. Cannot overlap with “info-needed”, “open-for-dev”, “in-progress”, “code-review” or “pending-merge” or “blocked”.
| status/open-for-dev | An issue has had its specification reviewed and confirmed. Waiting for an engineer to accept the issue and take it into active development.  Cannot overlap with “info-needed”, “analyzing”, “in-progress”, “code-review, “pending-merge” or “blocked”.
| status/in-progress | This issue has been taken by an engineer and is under active development. Cannot overlap with “info-needed”, “analyzing”, “open-for-dev”, “code-review”, “pending-merge” or “blocked”.
| status/code-review | This issue has a pull request posted for it and is awaiting code review completion by the community.  Cannot overlap with “info-needed”, “analyzing”, “open-for-dev”, “in-progress”, “pending-merge” or “blocked”.
| status/pending-merge | This issue has completed development and awaiting authorization to be merged into master. Sometimes issues can be completed, but are placed on hold to merge in "info-needed", "analyzing", "open-for-dev", "in-progress", "code-review" or "blocked". Issues with a `pending-merge` label need to reference the PR(s) that are pending.
| status/blocked | Issue that can’t be moved forward. Must include a comment on the reason for the blockage. If it’s blocked because it depends on another issue then it should include a link to the issue it depends on.Cannot overlap with “info-needed”, “analyzing”, “open-for-dev”, “in-progress”, “code-review” or “pending-merge”.
### Dev Open Pull Request Status
| Label        | Description
| ------------ |-------------
| status/work-in-progress | This PR is not ready to be merged. There is additional testing, development or input required.
| status/merge-ready | All reviews have been finalized. The PR can be merged into master if merges are being accepted according to sprint or milestone plan.
### Sprint Status
| Label        | Description
| ------------ |-------------
| sprint/current-sprint | Issue is being worked in the current sprint.
| sprint/next-sprint | Issue is planned to be worked in the next sprint.
### Team Assignments
| Label        | Description
| ------------ |-------------
| team/ide | Issue to be taken by the IDE team.
| team/enterprise | Issue to be taken by the enterprise features team.
| team/plugin | Issue to be taken by the plugin development team.
| team/production | Issue to be taken by the production readiness team.
| team/platform | Issue to be taken by the platform team.
| team/pm | Issue to be taken by the product management team.
