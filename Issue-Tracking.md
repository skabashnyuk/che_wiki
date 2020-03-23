This page describes how we track issues in the `eclipse/che` repository.

## Issue Labels
The Eclipse Che project relies heavily on [issue labels](https://github.com/eclipse/che/wiki/Labels) to communicate status and responsibility. Labels are defined in a separate doc.

## Issue Triage

New issues are automatically labeled with [*status/need-triage*](https://github.com/eclipse/che/labels/status%2Fneed-triage) by Che bot. Those issues need to be reviewed by a project committer (the curator) that will set [the issue severity](https://github.com/eclipse/che/wiki/Labels#bug-severities) and [area labels](https://github.com/eclipse/che/wiki/Labels#areas). We call it the triage process.

### Triage process

All issues labelled [*status/need-triage*](https://github.com/eclipse/che/labels/status%2Fneed-triage) are reviewed daily by a curator and the process to triage an issue consist in:

1. Verify that:
    - the issue is a not **duplicate**
    - the issue has **all the needed informations**
    - if it's a bug, it's **reproducible**
2. Add the [severity label](https://github.com/eclipse/che/wiki/Labels#bug-severities)
3. Add the [area label](https://github.com/eclipse/che/wiki/Labels#areas)
4. If appropriate set the label **[good first issue](https://github.com/eclipse/che/labels/good%20first%20issue)**

Once the triage is done the curator removes the label [*status/need-triage*](https://github.com/eclipse/che/labels/status%2Fneed-triage).

At the end of its working day the curator reports the triage summary in the [Eclipse Che mattermost channel](https://mattermost.eclipse.org/eclipse/channels/eclipse-che). 

### Triage curators

The curator changes every day and we are currently doing a weekly rotation:

- Monday: @ibuziuk
- Tuesday: @l0rd
- Wednesday: @benoitf
- Thursday: @tsmaeder
- Friday: @tolusha

This curators list changes often. To be part of it (even for one week only) committers can request it on [Eclipse Che mattermost channel](https://mattermost.eclipse.org/eclipse/channels/eclipse-che) or with an email at che-dev@eclipse.org mailing list.

### Triage FAQ

**What query should we use for looking at incoming issues?**
We should look for:
* Issues opened today: “is:issue is:open created:>=YYYY-MM-DD”
* [Issues labelled status/need-triage](https://github.com/eclipse/che/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+label%3Astatus%2Fneed-triage) 
* [Issues with more information needed](https://github.com/eclipse/che/issues?q=is%3Aopen+is%3Aissue+label%3Astatus%2Finfo-needed)
* [Issues waiting for analysis](https://github.com/eclipse/che/issues?q=is%3Aopen+is%3Aissue+label%3Astatus%2Fanalyzing)

**Should the curator try to reproduce all the issues?**
The curator doesn’t have the time to reproduce every issue. If it takes more than 15 min he should delegate it to a team leader. We do that labelling the issue as “team/xyz” + “status/2Fanalyzing” and assigning it to the team lead.

**Should the curator set the issue milestone?**
The curator should not set the issue milestone but, if the issue is a blocker, it should be part of current milestone. If it’s a P1 or P2 it depends on the team bandwidth (have they finished working on other P1s/P2s?) and on the risk of regressions. That said the curator may not be able to determine if it’s a blocker or not (ask @l0rd, @davidfestal @benoitf in that case) and if the corresponding team has bandwidth to work on it during the current sprint (just assign it to “team/xyz” or to a TL in that case).
