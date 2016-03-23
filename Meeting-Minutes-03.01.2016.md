Here are the notes of product meeting  March 1st, 2016.

######TOPICS DISCUSSED:
1. Status on Codenvy OnPrem readiness for EclipseCon
2. EclipseCon Support Team 
3. Goals for 4.0
4. Codenvy SaaS Phase 1
5. Handling of issues between JIRA/GitHub
6. Next Sprint pre-planning
7. Other
    - Pre-check during build of module
    - Automated changlog

#####ACTION ITEMS:
- Document analytics requirements for Codenvy Saas Phase1 (Tyler)
- Send emails for pre-planning (Stévan + TL)
- Update Che wiki with roadmap + meeting notes (Stévan)

######IMPORTANT POINTS ON TOPIC DISCUSSED:

**1. Status on Codenvy OnPrem readiness for EclipseCon**

Filter: https://jira.codenvycorp.com/issues/?jql=labels%20%3D%20eclipse-con16

We will handle a RC9 release and another one with will include the new crane loader. Probably, we will do other releases during the week to get the latest changes and stability fixes.

Separately, we need to publish RC9 as a released milestone on Eclipse. The release has been prepared and is ready to be uploaded.
https://projects.eclipse.org/projects/ecd.che/releases/4.0.0


**2. Eclipse Con Support Team**

Cherkassy is off on Tuesday 8th March, but we'll have to support Eclipse Con.
- Keynote Tues (most important)
- Rehearsal: 7.00 ET (4.00PT)
- Keynote: 9.30 ET (6.30PT) - 10.30 ET (7.30PT)

Booth Demos
- Mon: 9.00 ET(6.00 PT) - 17.00 ET(14.00 PT)
- Tues: 10.30 ET(7.30 PT) - 19.00 ET(16.00 PT)
- Wed: 10.00 ET(6.00 PT) - 17.30 ET(14.00 PT)
- Thu: 10.00 ET (7.00 PT) - 15.00 ET(12.00 PT)

Infra team will provide another server, "just in case" and demo factory will need to be replicated on that server.


**3. Goals for 4.0**

https://jira.codenvycorp.com/secure/Dashboard.jspa?selectPageId=16956

* **Rework Project API with new VFS**

Will be ready to be merged during the next sprint 

* **Microsoft VSTS devops flow use cases**

Coming along but the bottleneck is on the factories bug that we have on onprem.	

* **Enhanced silky smooth loadings and transitions experience**

New animation has been designed. Currently in progress in Plugin team. For factory, the PR is in progress.

* **Change project creation flow**


1 bug is remaining and in progress	50/52

* **Consoles panel** 

Done. We are separately, improving the experience to get a terminal (new icon / entry menu in Run)


**4. Discussion on Codenvy Saas Phase 1**

First version of the specification has been written and share to the team. 
And epic for phase 1: https://jira.codenvycorp.com/browse/CODENVY-134

Phase 1:
Tyler will provide details about analytics requirements for the Phase1.


**5. Handling issues between jira/github**

The installation of the TaskTop product is still in progress and is needing some scripts to keep in sync the issue between jira/github.

At this moment, we are manually keeping in sync the issue between GitHub and Jira. We handle the way from Jira to GitHub with a tool. And issues are manually ported from GitHub to Jira after having confirmation from Support.

We are expecting script and use of TaskTop tool later this week, after the work from Dmitry;

**6. Next Sprint pre-planning**

For the upcoming sprint, the priorities have been emphased:
- any kind of bugs that prevent to release 4.0.0
- any features from 4.0.0 backlog not yet planned/done in current sprints
- work on 4.1.0 requirements

**7. Others**
- *Pre-check dependencies when building*
We have some build failure when some dependencies are not installed on the community user's computer, for example, if NPM is not installed the whole build will fail. 
Each modules is having its own set of dependencies. By using maven profile, we will skip the build of a module and download it if we detect absence of dependencies during pre-check. 

- *Automated tool to build changelog*
A tool has been setup to automatically build the Che changelogs like this https://github.com/eclipse/che/releases/tag/4.0.0-RC9
The used tool is the following one: