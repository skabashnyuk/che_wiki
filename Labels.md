## Issue Labels
The Eclipse Che project relies heavily on [issue labels](https://github.com/eclipse/che/labels) as a way to communicate status and responsibility.

### New contributors
The following labels are for issues and pull request that new contributors can start with.
They will appear in the https://github.com/eclipse/che/contribute page.

| Label        | Description
| ------------ |-------------
| `good first issue`| Community, this issue looks easy to start with for a new contributor. Just take it. We'll help you!
| `help wanted`| Community, our teams are fully engaged on other issues. Feel free to take this one. We'll help you!


### [Issue Types](https://github.com/eclipse/che/labels?q=kind)

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

### [Areas](https://github.com/eclipse/che/labels?q=area)
Issues related to a specific functional area of Che. https://github.com/eclipse/che/labels?q=area


### [Bug Severities](https://github.com/eclipse/che/labels?q=severity) 
| Label        | Description
| ------------ |-------------
| `severity/blocker`| Causes system to crash and be non-recoverable or prevents Che developers from working on Che code.  Must be resolved immediately. Can only be applied to `kind/bugs`.
| `severity/P1`| Has a major impact to usage or development of the system. Issues / PRs with P1 status should be prioritized during sprint planning. Can be applied to all kinds of issues. Not all issues need a severity. If an enhancement or bug will take >1 sprint to address consider using the `roadmap/*` labels instead.
| `severity/P2`| Has a minor but important impact to the usage or development of the system. Should be considered when planning sprints. Can be applied to all kinds of issues. Not all issues need a severity. If an enhancement or bug will take >1 sprint to address consider using the `roadmap/*` labels instead.

### [Issue Level](https://github.com/eclipse/che/labels?q=level)
| Label        | Description
| ------------ |-------------
| `level/beginner` | A relatively easy issue that's well suited to being addressed by a pull request from the community.
| `level/intermediate` | A more advanced issue that is open to a pull request from a community member with more experience in Che.
| `level/advanced` | A challenging issue that is complicated and needs help from a community member with domain experience.

### [Dev Open Issue Status](https://github.com/eclipse/che/labels?q=status)
| Label        | Description
| ------------ |-------------
| `status/need-triage` | An issue that needs to be prioritized by the triage team.
| `status/info-needed` | More information is needed before the issue can move into the “analyzing” state for engineering.
| `status/analyzing` | An issue has been proposed and it is currently being analyzed for effort and implementation approach.
| `status/open-for-dev` | An issue has had its specification reviewed and confirmed. Waiting for an engineer to accept the issue and take it into active development.
| `status/in-progress` | This issue has been taken by an engineer and is under active development.
| `status/code-review` | This issue has a pull request posted for it and is awaiting code review completion by the community.
| `status/blocked` | Issue that can’t be moved forward. Must include a comment on the reason for the blockage. If it’s blocked because it depends on another issue then it should include a link to the issue it depends on.

### [Issue Lifecycle ](https://github.com/eclipse/che/labels?q=lifecycle)
| Label        | Description
| ------------ |-------------
| `lifecycle/stale` | Indicates an issue or PR has remained open with no activity and has become stale.
| `lifecycle/frozen` | Indicates that an issue or PR should not be auto-closed due to staleness.
| `lifecycle/rotten` | Denotes an issue or PR that has aged beyond stale and will be auto-closed.
| `lifecycle/active` | Indicates that an issue or PR is actively being worked on by a contributor.



### [Sprint labels](https://github.com/eclipse/che/labels?q=sprint)
| Label        | Description
| ------------ |-------------
| `sprint/current-sprint` | Issue is being worked in the current sprint.
| `sprint/next-sprint` | Issue is planned to be worked in the next sprint.

### [Team Assignments](https://github.com/eclipse/che/labels?q=team)
| Label        | Description
| ------------ |-------------
| `team/ide` | Issue to be taken by the IDE team (working on Che-theia plugins).
| `team/ide2` | Issue to be taken by the IDE2 team (working on Che-theia plugins and extensibility).
| `team/osio` | Issue to be taken by the che.openshift.io team (working on the integration of Che in che.openshift.io).
| `team/languages` | Issue to be taken by the languages development team.
| `team/che-qe` | Issue to be taken by the QE development team.
| `team/platform` | Issue to be taken by the platform team.
| `team/pm` | Issue to be taken by the product management team.

### [Pull Request Target](https://github.com/eclipse/che/labels?q=target)
| Label        | Description
| ------------ |-------------
| `target/branch` | Indicates that a PR will be merged into a branch other than master. When merging to master branch `target/` label should not be used as it is an assume default target for most PRs.
| `target/che6` | Indicates that a PR or an issue will be merged into che6.
| `target/che7` | Indicates that a PR or an issue will be merged into che7.
| `target/che7GA` | Indicates that a PR or an issue is targetting 7.0.0-GA.

### [Test failures](https://github.com/eclipse/che/labels?q=selenium)
| Label        | Description
| ------------ |-------------
| `selenium/failure` | Issues that is related to a Selenium failures reported by our CI platform and our QE team.

