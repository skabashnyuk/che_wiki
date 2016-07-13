Eclipse Che has generational advances (A.x.x), major releases with features (x.A.x), and bug fix releases (x.x.A). Each release is associated with a milestone target. We develop in two week agile iterations with a milestone release attempted at the end of each sprint.

# Roadmap
The team has a 6 month high level [Roadmap]() which defines the themes, features and technical debt to be addressed in the timeframe.

# Milestones
We will work in two-week iterations on the items in the roadmap. We begin a milestone on a Thursday and end on a Wednesday. The target is to make a published milestone release at the end of each iteration cycle. We start iterations mid-week to allow for the possibility to have the release process flow into the following iteration and still complete within the same calendar week where the iteration completed.

At the end of each iteration, we want to have a version of Che that can be used by the Che community. The project leaders will decide if a milestone release within GitHub becomes a marketing "ship" event, where we have completed the Eclipse IP process and do a broad-based marketing update with the release notes.  

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
