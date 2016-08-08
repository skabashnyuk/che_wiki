This page describes how we track issues in the `eclipse/che` repository.

## Popular Queries
### Triage and Unprocessed Issue Queries
[Issue Triage](https://github.com/eclipse/che/issues?utf8=%E2%9C%93&q=is%3Aopen%20no%3Aassignee%20-label%3Akind%2Fquestion%20-label%3Akind%2Fenhancement%20-label%3Akind%2Fepic%20-label%3Akind%2Ftask%20-label%3Akind%2Fdocs%20-label%3Aseverity%2Fblocker%20-label%3Astatus%2Finfo-needed%20-label%3Astatus%2Fanalyzing%20-label%3Astatus%2Fopen-for-dev%20-label%3Astatus%2Fin-progress%20-label%3Astatus%2Fcode-review%20-label%3Astatus%2Fpending-merge%20-label%3Astatus%2Fblocked%20-label%3Ateam%2Fide%20-label%3Ateam%2Fenterprise%20-label%3Ateam%2Fplugin%20-label%3Ateam%2Fproduction%20-label%3Ateam%2Fplatform%20-label%3Ateam%2Fpm%20-label%3Astatus%2Fwork-in-progress%20-label%3Astatus%2Fmerge-ready%20-label%3Asprint%2Fcurrent-sprint%20-label%3Asprint%2Fnext-sprint)

[Questions for Support](https://github.com/eclipse/che/labels/kind%2Fquestion)


### Milestone Status Queries
The set of queries for a milestone is listed in the milestone details which can be found on the [milestone plans](https://github.com/eclipse/che/wiki/Milestone-Plans) page.

## Issue Labels
The Eclipse Che project relies heavily on [issue labels](https://github.com/eclipse/che/wiki/Labels) to communicate status and responsibility. Labels are defined in a separate doc.

## Issue Triage
New issues are processed and assigned a label for follow-up by the Triage owner, the Triage owner should try and keep the number of unlabelled issues to a minimum at all times while responsibly labelling each issue. A new Issue Triage owner is assigned each week (there will be a rotating schedule and if the person is in development they will be exempted from development tasks for that week - instead their primary role will be working as a support engineer).

The Issue Triage query contains 
- all open issues or pull requests that...
- are unlabelled, or are non-blocker bugs...
- and have no one assigned...
- and aren’t labeled with a team/... label.

For each issue in the list, the Triage owner will analyze the issue and discuss it as necessary with other members of the team then assign a label to it as follows:
- Answerable issues > Triage owner should solve and close them.
- Invalid issues > close them and explain the reason.
- Duplicate issues > close them and add a comment: "Duplicates {issue link}."
- General questions > label them with “kind/question”.
- Docs issues > label with “kind/docs”.
- Enhancement requests > label them with “kind/enhancement” and assign to one of the team lead or product owners.
- Technical tasks and to-dos > label them with “kind/task” and assign to one of the team lead or product owners.
- Bugs > label with "kind/bug" and assign to one of the team lead or product owners. Ensure that bugs adhere to the bug template. Note that the label "severity/blocker" should only be used for bugs assigned to a milestone and only by project committers.

Technical issues assigned to a team lead that do not have a status/... label are considered unprocessed (you can find unprocessed issues queries in the common queries section of this page). To complete them the Team Lead (or optionally Triage owner) must:
- Assign it the appropriate status/ label and optionally add sprint/current-sprint label and add it to the milestone.
- Edit the title to improve it (if needed).
- Follow-up with the author (if needed). 

Team Leads should keep their unprocessed backlog as small as possible at all times and try to move issues as quickly as possible to "status/open-for-dev".

## Consistent Milestones
To enable planning across repositories, we require that all related Che repositories, such as `eclipse/che-parent` define identical milestones.


