Eclipse Che has generational advances (A.x.x), major releases with features (x.A.x), and bug fix releases (x.x.A). Each release is associated with a milestone target. We develop in two week agile iterations with a milestone release attempted at the end of each sprint.

# Roles
There are four roles that define responsibilities for managing our process:
1. Contributors: Anyone who participates in our GitHub forums or issues a pull request. Anyone can be a contributor.

2. Committers: Someone with committer rights to our repositories. Any individual that gets two major PRs merged is nominated by a project leader to become a committer. Committers must submit at least two PRs each year to maintain their committer status. Committers also act as PR "reviewers" whose +1 consent is required for a PR to be merged.

3. Maintainers: Responsible for managing issue backlog and ensuring that the development and pull request process is followed. One maintainer is a mandatory reviewer on every pull request. Their +1 consent must be provided for the pull request to be merged. If the pull request is from a contributor without merge rights, the maintainer will perform the merge. In the rare event that discussions on pull requests or issues lead to a deadlock on which direction should be taken, then a maintainer will decide the path forward. Maintainers have a difficult job in that they are ultimately responsible for ensuring the stability and maintainability of the code base. Current maintainers are Sergii Kabashnyuk, Roman Iuvshin, Vitalii Parfonov, Anna Shumalova, Florent Benoit, Stevan LeMeur, and Mario Loriedo.

4. Project Leaders: Responsible for governing the project, setting the 6 month roadmap, ensuring that the development process reflects our project's values and objectives, and nominating individuals to become committers or maintainers. Current project leaders are Tyler Jewell and Gennady Azarenkov.

# Roadmap
Project leaders maintain a 6 month forward looking [Roadmap](https://github.com/eclipse/che/wiki/Roadmap) which defines the themes, features and technical debt to be addressed in the time frame.

# Milestones
We work in three-week iterations. We begin a milestone on a Thursday and end on a Wednesday. We perform a milestone release at the end of each iteration cycle. 

At the end of each iteration, we version and release Che for community use. The project leaders will decide if a milestone release within GitHub becomes a marketing "ship" event, where we have completed the Eclipse IP process and do a broad-based marketing update with the release notes.  

The work done in a milestone is captured in the milestone plan (see [Milestone Plans]()). The feature highlights, bugs fixed, and technical debt tasks completed are all contained in the release notes.

# Planning
Within any given time period we work on two milestones: the immediate upcoming milestone and the one that follows it.

We handle planning for Eclipse Che in two ways:
*  For the immediate upcoming milestone, we will only accept features who have a pending pull request which has been tested and ready for merge. This will allow the entirety of the iteration to be dedicated to hardening the system and resolving any infrastructure or regressions that appear. Che maintainers may optionally accept pull requests that are initiated during a milestone if they are deemed to have a low risk to destabilizing the code base for the release.

* For the milestone after the upcoming milestone, we prioritize features to implement and bugs to fix to be worked on during the current milestone so that it can have a set of pending pull requests ready when the following milestone starts. 

One week before the start of a milestone, we hold a pre-planning meeting where we define the milestone plans for milestone X and X+1. Bugs and features that are targeted for each milestone are assigned to the milestone for the iteration.

TODO: Document how we include bugs, features into a milestone.  
TODO: Add any specific tags used in the tracking.   
TODO: Provide "definition of done" check list.   
TODO: Provide location for pre-planning meeting.  

# Triage
Bugs and features will be assigned a milestone and within a milestone they will be assigned a priority. The priority dictates the order in which issues should be addressed. A critical bug (something that we think is critical for the milestone) is to be addressed before the other bugs.

To find out when a bug fix will be available in an update, please check the milestone that is assigned to the issue.

TODO: Provide a best practices page around issue tracking

# Weekly
Each week we will manage work items, cross off completed features and triaging bugs. At the end of the milestone we strike for 0 bugs and 0 issues assigned to the milestone. Some bugs and features will then either be postponed to later milestones, moved to the back of the backlog, or a choice will be taken to delay making the release until all issues are resolved.

# Release Readiness
Since the upcoming milestone generally does not have net new features and is primarily concerned with stabilization, we focus our testing on the test plans provided in the milestone plans. We then will fix the critical bugs for that milestone.  During this cycle, we make builds available nightly using our Docker image `codenvy/che:nightly` or by downloading a [nightly ZIP build](https://install.codenvycorp.com/che/).

When all of the critical bugs have been resolved, we tag the release and produce a final stable build. Before we publish the stable release, we manually execute the smoke test on all supported platforms.

TODO: Roman to document the smoke test execution plan.

# Deprecation Policy
Plans to deprecate will be outlined in issues (where possible and appropriate) for community feedback. Once feedback has been addressed deprecation schedule will be announced on che-dev mailing list and in the changelog. Discussed API deprecation should stay in product for at least 1 month(2 sprints) before removal. Deprecation notification will be included in release notes and changelog release(s) prior to release where API is removed. In cases where the deprecation may affect white label customers, the team leads will notify PM's (Brad and James) in advance so that those customers can be notified.
