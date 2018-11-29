Development Process

Eclipse Che has generational advances (A.x.x), major releases with features (x.A.x), and bug fix releases (x.x.A). Each release is associated with a milestone target. We develop in three week agile iterations (Sprint) with a milestone release attempted at the end of each sprint.

# Roles
There are six roles that define responsibilities for managing our process:

1. **Contributors**: Anyone who participates in our GitHub forums or issues a pull request. Anyone can be a contributor. Contributors with merge rights (committers) will merge their own PRs after all reviews have completed. Contributors without merge rights will have a Maintainer merge their PR.

2. **Committers**: Someone with committer rights to our repositories. Any individual that gets two major PRs merged can be nominated by another committer to become a committer. Committers must submit at least two PRs each year to maintain their committer status. Committers also act as PR "reviewers" whose +1 consent is required for a PR to be merged.

3. **Reviewers**: A committer assigned to participate in a PR review. Reviewers can be asked to review any part of the product including code review, code formatting, change log, release notes, documentation, unit test verification, and the marketing material alterations that must exist when a PR is merged. Reviewers are assigned to a PR by the PR initiator, the Triager, or Maintainers. Reviewers are expected to ensure that our standards for code structure, format, and maintenance are met before offering consent.

4. **Triager**: Someone selected by the project leader responsible to review new PRs, apply necessary labels, assigns reviewers, and identifies the maintainer / product area for the PR. The triager is expected to review all new open PRs daily. The [CODEOWNERS](https://github.com/eclipse/che/blob/master/.github/CODEOWNERS) file automatically assigns recommended reviewers to new PRs. This list is reviewed and expanded or accepted by the Triager.

5. **Maintainers**: Responsible for managing issue backlog, ensuring long term code quality for a product area, ensures that our PR process is followed, and provides technical decision making on areas where consensus does not exist. Maintainers are responsible for periodically reviewing the open PRs and issue backlog for their product area to ensure that the PR reviewer list is complete, issues are ordered properly in the backlog, and that reviewers are providing substantive reviews. Maintainers need to do the scheduling and the communication of the PR’s review - this would provide in less than 3 business days. Maintainer usually listed as a [CODEOWNER](https://help.github.com/articles/about-codeowners/) of particular area and included to PR Reviewer list by default.

Maintainers:
* IDE: Vitalii Parfonov (@vparfonov), Artem Zatsarynnyi (@azatsarynnyy)
* Language Servers, IDE Plugins: Dmitro Kuleshov (@dkuleshov),  Evgen Vidolob (@evidolob)
* Platform: Sergii Kabashnyuk (@skabashnyuk), Alex Garagatyi (@garagatyi)
* Kubernetes: Mario Loriedo (@l0rd), Gorkem Ercan (@gorkem)
* Dashboard: Anna Shumilova (@ashumilova), Florent Benoit (@benoitf)
* QA Automation: Anatoliy Bazko (@tolusha)
* Utilities (CLI, devops, etc): Roman Iuvshin (@riuvshin), Eugene Ivantsov (@eivantsov)
* Docs: Stevan Lemeur (@slemeur), Eugene Ivantsov (@eivantsov), Brad Micklea (@bmicklea)
* Architecture: Gennady Azarenkov (@gazarenkov)

If the pull request is from a contributor without merge rights, the maintainer will perform the merge. 

6. **Project Leaders**: Responsible for governing the project, setting the 6 month roadmap, ensuring that the development process reflects our project's values and objectives, and nominating individuals to become maintainers. Current project leaders are Tyler Jewell and Gennady Azarenkov.

# Roadmap
Project leaders maintain a 6 month forward looking [Roadmap](https://github.com/eclipse/che/wiki/Roadmap) which defines the themes, features and technical debt to be addressed in the time frame.

# Milestones
We work in three-week iterations called Sprint. We begin a Sprint on a Thursday and end on a Wednesday. We perform a milestone release (potentially shippable product) at the end of each Sprint. 

At the end of each iteration, we version and release Che for community use. The project leaders will decide if a milestone release within GitHub becomes a marketing "ship" event, where we have completed the Eclipse IP process and do a broad-based marketing update with the release notes.  

The work done in a milestone is captured in the milestone plan (see [Milestone Plans]()). The feature highlights, bugs fixed, and technical debt tasks completed are all contained in the release notes.

# Planning
We make commitments for the current milestone in a three-week sprint. While working on the current sprint we pre-plan (prepare) the next milestone to have enough context for planning it. We have a planning meeting before a sprint starts with a pre-planning discussion about one week before the sprint begins.

Issues with the `sprint/current-sprint` label are commitments to be part of the upcoming milestone assuming development is able to complete a PR merge. Issues with the `sprint/next-sprint` label are items that are under consideration under the sprint pre-planning exercise.

We handle planning for Eclipse Che in two ways:
*  For the immediate upcoming milestone, we will only accept features who have a pending pull request which has been reviewed, tested and ready for merge. This will allow the entirety of the iteration to be dedicated to hardening the system and resolving any infrastructure or regressions that appear. Che maintainers may optionally accept pull requests that are initiated during a milestone if they are deemed to have a low risk to destabilizing the code base for the release.

* For the milestone after the upcoming milestone, we prioritize features to implement and bugs to fix to be worked on during the current milestone so that it can have a set of pending pull requests ready when the following milestone starts. 

# Triage
Bugs are assigned a priority based upon the impact that they have to end users. The priority dictates the order in which issues should be addressed. A critical bug (something that we think is critical for the milestone) is to be addressed before the other bugs.

To find out when a bug fix will be available in an update, please check the milestone that is assigned to the issue.

# Weekly
At the end of a milestone we strive for 0 bugs and 0 issues remaining open that were assigned to the milestone. Some bugs and features may be postponed to later milestones, moved back into the backlog, or on rare occasions delay the release while issues are resolved.

# Release
A release is performed at the end of each sprint. The release procedure is automated as part of the CI/CD pipeline. We use maven to tag / compile binaries from the source code and Docker to build and tag images.

During release we create a release branch from master where the release is performed. This allows us to apply bugfixes if needed, without freezing the master branch and preventing developers from merging new changes. 

If a bugfix release is needed, we reuse the appropriate release branch.
 
Once a release is done we deploy the new version to staging where we run a final QA cycle against the new version. The release could be blocked and moved to end of the next sprint if we have blocker bugs.

## Release notes
We publish release notes on the web site for each release with highlights to `new & noteworthy` changes.

1. After each release the notes maintainer creates the notes for the next release named `Major_Minor.md` under [this folder](https://github.com/eclipse/che-docs/tree/master/release-notes) on the repository.
2. Every PR for a new and noteworthy change require another PR with changes to this file with description and any visuals
3. Notes maintainer and Contributors review and merge this PR.
4. As part of the release Notes maintainer and PM does a last review.
5. Release notes are published to the web site.

### Roles 
* Release Notes Maintainer - Eugene Ivantsov (backup Gennady)
* Product Manager - Steven LeMeur (backup Brad Micklea)  

# Nightly builds
Nightly builds are generated on daily basis and available as docker images with the
tag:nightly.

# Deprecation Policy
Plans to deprecate will be outlined in issues (where possible and appropriate) for community feedback. Once feedback has been addressed deprecation schedule will be announced on che-dev mailing list and in the changelog. Discussed API deprecation should stay in product for at least 2 sprints before removal. Deprecation notification will be included in release notes and changelog release(s) prior to release where API is removed. In cases where the deprecation may affect white label customers, the team leads will notify PM's in advance so that those customers can be notified.